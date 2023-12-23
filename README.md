# sysman
System Manager written in Go with a webgui using HTMX

## Why?
I've always wanted to write a system manager. Something that is much simpler
then webmin/virtualmin, has better service integrations then cockpit, but
doesn't limit you to only using the gui.

## Requirements
I will consider this a success when:
- A database isn't needed to login to the system
- Integrated services doesn't just mean start a container (although you will
  most certainly be able to run containers). It will read configuration files
  directly in order to understand the system.
- Has a simple gui that enables advanced options in an easy to understand way
- Uses OpenAPI standards to be extensible

## OS Support
Needs CLI tools that support the following OS's:
- RHEL based systems, using RPM and DNF
- Debian based systems, using apt and dpkg
- NixOS based systems, modifying either configuration.nix or flakes machine
  definitions
- FreeBSD based systems, using pkg and ports

## Roadmap
Milestones before major versions:
- Before version 0.1
  - System status dashboard, with CPU usage, memory usage, network usage.
  - Export data via prometheus compatible metrics, but doesn't need prometheus
    or grafana to be a useful source of information
  - Ability to modify simple things for a system, with the minimum being:
    - Hostname change
    - Timezone change
    - Check for updates
    - Install updates
    - Find and install packages
- Version 0.2
  - View filesystems and get metrics from them
    - Support ext4, xfs, zfs and btrfs
  - LVM support
    - Ability to create LVM managed volumes, with advanced options like
      deduplication, compression
  - NFS support
    - Mount NFS and define NFS shares
  - Samba filesharing
  - Webdav filesharing
  - Disk management
    - Create and modify partitions
      - Parted as backend simplifies the setup and can be scriptable
    - Create new filesystems
      - Support all of the above filesystems
      - Simple checkbox method for supported options
      - Sane defaults for each filesystem
    - Set mount options for each filesystem
- Version 0.3
  - Networking
    - Linux;
      - Modify interfaces, setting up either DHCP or static addresses
        - Support multiple addresses per interface
        - Set VLAN configurations
        - Create/modify bonds, bridges, macvlan, etc.
      - Use network manager, nixos configuration, and basic ip command
      - DNS settings, recursive DNS resolver locally
    - FreeBSD;
      - Modify interfaces, setting up either DHCP or static addresses
        - Support multiple addresses per interface
        - Set VLAN configurations
        - Create/modify bonds, bridges, etc.
      - Use ifconfig and save configuration in rc.conf
      - DNS settings, recursive DNS resolver locally
    - Metrics per interface
- Version 0.4
  - Boot management on all supported systems
    - Change defaults for grub to add and remove options from kernel cmdline
    - Ensure changes are applied properly after making modifications
    - ZFS: Boot environments support
  - Disk
