---
title: "networking error on startup, works with restart"
date: 2009-08-17
forum: General Help
---

### Post by duddyi on 2009-08-17
recently on a system restart we are forced to activate our networking by manually entering the command

/etc/init.d/networking restart

otherwise eth0 is not defined or active.

below is our full log for a restart - can anyone identify from this what the problem is and how we can resolve this
thanks
Duddy

Aug 17 16:42:08 sugarbackup-desktop syslogd 1.5.0#2ubuntu6: restart.
Aug 17 16:42:08 sugarbackup-desktop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Aug 17 16:42:08 sugarbackup-desktop kernel: Cannot find map file.
Aug 17 16:42:08 sugarbackup-desktop kernel: Loaded 52525 symbols from 84 modules.
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f55ac00 (usable)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 000000007f55ac00 - 000000007f55ec00 (ACPI NVS)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 000000007f55ec00 - 000000007f560c00 (ACPI data)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 000000007f560c00 - 0000000080000000 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] last_pfn = 0x7f55a max_arch_pfn = 0x100000
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] RAMDISK: 3781e000 - 37fefd33
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] DMI 2.5 present.
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] ACPI: XSDT 000FD0F3, 005C (r1 DELL    B9K           15 ASL        61)
Aug 17 16:42:08 sugarbackup-desktop kernel: [    0.000000] ACPI: FACP 000FD20B, 00F4 (r3 DELL    B9K           15 ASL        61)
Aug 17 16:42:08 sugarbackup-desktop avahi-daemon[4713]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: DSDT FFF575E8, 3346 (r1   DELL    dt_ex     1000 INTL 20050624)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Successfully dropped root privileges.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: FACS 7F55AC00, 0040
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: avahi-daemon 0.6.23 starting up.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: SSDT FFF5AA4F, 00AC (r1   DELL    st_ex     1000 INTL 20050624)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Successfully called chroot().
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: APIC 000FD2FF, 0092 (r1 DELL    B9K           15 ASL        61)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Successfully dropped remaining capabilities.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: BOOT 000FD391, 0028 (r1 DELL    B9K           15 ASL        61)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: No service file found in /etc/avahi/services.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: MCFG 000FD3B9, 003E (r1 DELL    B9K           15 ASL        61)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.60.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: HPET 000FD3F7, 0038 (r1 DELL    B9K           15 ASL        61)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: New relevant interface eth0.IPv4 for mDNS.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] ACPI: SLIC 000FD42F, 0176 (r1 DELL    B9K           15 ASL        61)
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Network interface enumeration completed.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] 1141MB HIGHMEM available.
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Registering new address record for fe80::221:9bff:fe72:90ac on eth0.*.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Registering new address record for 192.168.0.60 on eth0.IPv4.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Aug 17 16:42:09 sugarbackup-desktop avahi-daemon[4713]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000]   low ram: 00000000 - 38000000
Aug 17 16:42:09 sugarbackup-desktop kernel: [    0.000000]   bootmap 00008000 - 0000f000
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #4 [003781e000 - 0037fefd33]          RAMDISK ==> [003781e000 - 0037fefd33]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000] found SMP MP-table at [c00fe710] 000fe710
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 17 16:42:10 sugarbackup-desktop avahi-daemon[4713]: Server startup complete. Host name is sugarbackup-desktop.local. Local service cookie is 258580420.
Aug 17 16:42:10 sugarbackup-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug 17 16:42:10 sugarbackup-desktop mysqld_safe[4836]: started
Aug 17 16:42:11 sugarbackup-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Aug 17 16:42:12 sugarbackup-desktop mysqld[4839]: 090817 16:42:10 [Warning] The syntax for replication startup options is deprecated and will be removed in MySQL 5.2. Please use 'CHANGE MASTER' instead.
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f55a
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Aug 17 16:42:12 sugarbackup-desktop mysqld[4839]: 090817 16:42:10  InnoDB: Started; log sequence number 0 43685
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007f55a
Aug 17 16:42:12 sugarbackup-desktop mysqld[4839]: 090817 16:42:10 [Warning] Neither --relay-log nor --relay-log-index were used; so replication may break when this MySQL server acts as a slave and has his hostname changed!! Please use '--relay-log=mysqld-relay-bin' to avoid this problem.
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000] On node 0 totalpages: 521465
Aug 17 16:42:12 sugarbackup-desktop mysqld[4839]: 090817 16:42:10 [Note] Slave SQL thread initialized, starting replication in log 'mysql-bin.000819' at position 3200656, relay log './mysqld-relay-bin.000109' position: 47182
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
Aug 17 16:42:12 sugarbackup-desktop mysqld[4839]: 090817 16:42:10 [Note] /usr/sbin/mysqld: ready for connections.
Aug 17 16:42:12 sugarbackup-desktop /etc/mysql/debian-start[4880]: Upgrading MySQL tables if necessary.
Aug 17 16:42:12 sugarbackup-desktop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Aug 17 16:42:12 sugarbackup-desktop mysqld[4839]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Aug 17 16:42:12 sugarbackup-desktop exportfs[5002]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "sugarlive:/".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Aug 17 16:42:13 sugarbackup-desktop kernel: [    0.000000]   Normal zone: 223300 pages, LIFO batch:31
Aug 17 16:42:13 sugarbackup-desktop /etc/mysql/debian-start[4984]: Looking for 'mysql' in: /usr/bin/mysql
Aug 17 16:42:14 sugarbackup-desktop mysqld[4839]: 090817 16:42:10 [Note] Slave I/O thread: connected to master 'slave_user@192.168.0.50:3306',  replication started in log 'mysql-bin.000819' at position 3200656
Aug 17 16:42:15 sugarbackup-desktop kernel: [    0.000000]   HighMem zone: 289617 pages, LIFO batch:31
Aug 17 16:42:16 sugarbackup-desktop /etc/mysql/debian-start[4984]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Aug 17 16:42:17 sugarbackup-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 17 16:42:18 sugarbackup-desktop /etc/mysql/debian-start[4984]: This installation of MySQL is already upgraded to 5.0.67, use --force if you still need to run mysql_upgrade
Aug 17 16:42:18 sugarbackup-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 17 16:42:19 sugarbackup-desktop /etc/mysql/debian-start[5064]: Checking for insecure root accounts.
Aug 17 16:42:20 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 17 16:42:20 sugarbackup-desktop /etc/mysql/debian-start[5083]: Triggering myisam-recover for all MyISAM tables
Aug 17 16:42:21 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 17 16:42:22 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
Aug 17 16:42:22 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
Aug 17 16:42:22 sugarbackup-desktop postfix/master[5116]: daemon started -- version 2.5.5, configuration /etc/postfix
Aug 17 16:42:24 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Aug 17 16:42:25 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
Aug 17 16:42:25 sugarbackup-desktop acpid: client connected from 5297[111:122] 
Aug 17 16:42:25 sugarbackup-desktop bluetoothd[5327]: Bluetooth daemon
Aug 17 16:42:25 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
Aug 17 16:42:25 sugarbackup-desktop NetworkManager: <info>  starting... 
Aug 17 16:42:25 sugarbackup-desktop bluetoothd[5327]: Starting SDP server
Aug 17 16:42:25 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
Aug 17 16:42:26 sugarbackup-desktop NetworkManager: <info>  eth0: driver is 'tg3'. 
Aug 17 16:42:27 sugarbackup-desktop acpid: client connected from 5410[0:0] 
Aug 17 16:42:27 sugarbackup-desktop bluetoothd[5327]: bridge pan0 created
Aug 17 16:42:28 sugarbackup-desktop anacron[5458]: Anacron 2.3 started on 2009-08-17
Aug 17 16:42:29 sugarbackup-desktop /usr/sbin/cron[5501]: (CRON) INFO (pidfile fd = 3)
Aug 17 16:42:29 sugarbackup-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
Aug 17 16:42:29 sugarbackup-desktop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Aug 17 16:42:29 sugarbackup-desktop bluetoothd[5327]: Starting experimental netlink support
Aug 17 16:42:29 sugarbackup-desktop anacron[5458]: Normal exit (0 jobs run)
Aug 17 16:42:29 sugarbackup-desktop /usr/sbin/cron[5748]: (CRON) STARTUP (fork ok)
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_21_9b_72_90_ac 
Aug 17 16:42:30 sugarbackup-desktop bluetoothd[5327]: Failed to find Bluetooth netlink family
Aug 17 16:42:30 sugarbackup-desktop /usr/sbin/cron[5748]: (CRON) INFO (Running @reboot jobs)
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  Trying to start the supplicant... 
Aug 17 16:42:30 sugarbackup-desktop bluetoothd[5327]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 17 16:42:30 sugarbackup-desktop gdmgreeter[5937]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  (eth0): preparing device. 
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 17 16:42:30 sugarbackup-desktop avahi-daemon[4713]: Withdrawing address record for 192.168.0.60 on eth0.
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  Setting system hostname to 'localhost.localdomain' (no default device) 
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 17 16:42:30 sugarbackup-desktop avahi-daemon[4713]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.60.
Aug 17 16:42:30 sugarbackup-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Aug 17 16:42:30 sugarbackup-desktop nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 17 16:42:30 sugarbackup-desktop avahi-daemon[4713]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Aug 17 16:42:30 sugarbackup-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000039000000
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: addresses count: 1
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000f0000
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_21_9b_72_90_ac, iface: eth0): well known
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 516880
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: (143913192) ... get_connections.
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] Kernel command line: root=UUID=171eb887-e087-4160-ac89-937dc98719ac ro quiet splash 
Aug 17 16:42:30 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: (143913192) ... get_connections (managed=false): return empty list.
Aug 17 16:42:30 sugarbackup-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 17 16:42:31 sugarbackup-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Aug 17 16:42:31 sugarbackup-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 17 16:42:31 sugarbackup-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Aug 17 16:42:31 sugarbackup-desktop kernel: [    0.000000] Initializing CPU#0
Aug 17 16:42:31 sugarbackup-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 17 16:42:31 sugarbackup-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 17 16:42:31 sugarbackup-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 17 16:42:31 sugarbackup-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Aug 17 16:42:31 sugarbackup-desktop NetworkManager: <info>  (eth0): now unmanaged 
Aug 17 16:42:31 sugarbackup-desktop kernel: [    0.000000] TSC: using PIT calibration value
Aug 17 16:42:31 sugarbackup-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Aug 17 16:42:31 sugarbackup-desktop kernel: [    0.000000] Detected 2194.477 MHz processor.
Aug 17 16:42:31 sugarbackup-desktop NetworkManager: <info>  (eth0): cleaning up... 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Aug 17 16:42:32 sugarbackup-desktop NetworkManager: <info>  (eth0): taking down device. 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] console [tty0] enabled
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 17 16:42:32 sugarbackup-desktop avahi-daemon[4713]: Withdrawing address record for fe80::221:9bff:fe72:90ac on eth0.
Aug 17 16:42:32 sugarbackup-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Memory: 2052504k/2086248k available (2572k kernel code, 32460k reserved, 1160k data, 424k init, 1168744k highmem)
Aug 17 16:42:32 sugarbackup-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] virtual kernel memory layout:
Aug 17 16:42:32 sugarbackup-desktop NetworkManager: <info>  Setting system hostname to 'sugarbackup-desktop' (from system configuration) 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Aug 17 16:42:32 sugarbackup-desktop nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Aug 17 16:42:32 sugarbackup-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] hpet clockevent registered
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4388.95 BogoMIPS (lpj=8777908)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Security Framework initialized
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] SELinux:  Disabled at boot.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] AppArmor: AppArmor initialized
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Mount-cache hash table entries: 512
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Initializing cgroup subsys ns
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Initializing cgroup subsys memory
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: L2 cache: 1024K
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: Processor Core ID: 0
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] using mwait in idle threads.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.017791] ACPI: Core revision 20080609
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.064619] ACPI: Checking initramfs for custom DSDT
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.437455] ENABLING IO-APIC IRQs
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.437628] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.477323] CPU0: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.480030] Booting processor 1/1 ip 6000
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Initializing CPU#1
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 4388.88 BogoMIPS (lpj=8777773)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: L2 cache: 1024K
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.564401] CPU1: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.564417] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568050] Brought up 2 CPUs
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568053] Total of 2 processors activated (8777.84 BogoMIPS).
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568074] CPU0 attaching sched-domain:
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568076]  domain 0: span 0-1 level MC
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568078]   groups: 0 1
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568084] CPU1 attaching sched-domain:
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568086]  domain 0: span 0-1 level MC
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568088]   groups: 1 0
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568159] net_namespace: 840 bytes
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568159] Booting paravirtualized kernel on bare hardware
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568270] Time: 15:41:49  Date: 08/17/09
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568297] NET: Registered protocol family 16
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] EISA bus registered
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] ACPI: bus type pci registered
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] PCI: MCFG area at e0000000 reserved in E820
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] PCI: Using MMCONFIG for extended config space
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568315] PCI: Using configuration type 1 for base access
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.568525] ACPI: EC: Look up EC in DSDT
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603689] ACPI: BIOS _OSI(Linux) query ignored
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603692] ACPI: DMI System Vendor: Dell Inc.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603693] ACPI: DMI Product Name: OptiPlex 360                 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603695] ACPI: DMI Product Version: 
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603697] ACPI: DMI Board Name: 0T656F
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603698] ACPI: DMI BIOS Vendor: Dell Inc.
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603700] ACPI: DMI BIOS Date: 08/12/2008
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603701] ACPI: Please send DMI info above to [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.603703] ACPI: If "acpi_osi=Linux" works better, please notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.617405] ACPI: Interpreter enabled
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.617407] ACPI: (supports S0 S1 S3 S4 S5)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.617423] ACPI: Using IOAPIC for interrupt routing
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:01.0: PME# disabled
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:02.0 reg 10 32bit mmio: [dfe00000, dfe7ffff]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:02.0 reg 14 io port: [ecd8, ecdf]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:02.0 reg 1c 32bit mmio: [dff00000, dfffffff]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:02.1 reg 10 32bit mmio: [dfe80000, dfefffff]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1b.0 reg 10 64bit mmio: [dfdfc000, dfdfffff]
Aug 17 16:42:32 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1b.0: PME# disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1c.0: PME# disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1d.0 reg 20 io port: [ff80, ff9f]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1d.1 reg 20 io port: [ff60, ff7f]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1d.2 reg 20 io port: [ff40, ff5f]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1d.3 reg 20 io port: [ff20, ff3f]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ff980800, ff980bff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1d.7: PME# disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.2 reg 10 io port: [fe00, fe07]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.2 reg 14 io port: [fe10, fe13]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.2 reg 18 io port: [fe20, fe27]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.2 reg 1c io port: [fe30, fe33]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.2 reg 20 io port: [fec0, fecf]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1f.2: PME# supported from D3hot
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] pci 0000:00:1f.2: PME# disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.681034] PCI: 0000:00:1f.3 reg 20 io port: [ece0, ecff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684060] PCI: bridge 0000:00:01.0 32bit mmio: [dfc00000, dfcfffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684128] PCI: 0000:02:00.0 reg 10 64bit mmio: [dfbf0000, dfbfffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684180] pci 0000:02:00.0: PME# supported from D3hot D3cold
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684185] pci 0000:02:00.0: PME# disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684220] PCI: bridge 0000:00:1c.0 32bit mmio: [dfb00000, dfbfffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684270] pci 0000:00:1e.0: transparent bridge
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684291] bus 00 -> node 0
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.684912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.685361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    0.685672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.368345] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.368706] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.369065] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.369460] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.369802] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.370173] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.370548] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.370891] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.371019] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.371019] pnp: PnP ACPI init
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.371019] ACPI: bus type pnp registered
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.378304] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.378307] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.398040] pnp: PnP ACPI: found 9 devices
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.398040] ACPI: ACPI bus type pnp unregistered
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.398040] PnPBIOS: Disabled by ACPI PNP
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.398040] PCI: Using ACPI for IRQ routing
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404044] NET: Registered protocol family 8
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404049] NET: Registered protocol family 20
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404074] NetLabel: Initializing
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404074] NetLabel:  domain hash size = 128
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404074] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404090] NetLabel:  unlabeled traffic allowed by default
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404098] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.404107] hpet0: 3 64-bit timers, 14318180 Hz
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.406784] tracer: 772 pages allocated for 65536 entries of 48 bytes
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.406787]    actual entries 65620
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.406875] AppArmor: AppArmor Filesystem Enabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.406896] ACPI: RTC can wake from S4
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.408044] Switched to high resolution mode on CPU 0
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.408445] Switched to high resolution mode on CPU 1
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.412062] system 00:01: ioport range 0xc00-0xc7f has been reserved
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447165] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447167] pci 0000:00:01.0:   IO window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447171] pci 0000:00:01.0:   MEM window: 0xdfc00000-0xdfcfffff
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447174] pci 0000:00:01.0:   PREFETCH window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447179] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447181] pci 0000:00:1c.0:   IO window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447185] pci 0000:00:1c.0:   MEM window: 0xdfb00000-0xdfbfffff
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447189] pci 0000:00:1c.0:   PREFETCH window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447195] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447197] pci 0000:00:1e.0:   IO window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447201] pci 0000:00:1e.0:   MEM window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447205] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447220] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447224] pci 0000:00:01.0: setting latency timer to 64
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447230] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447234] pci 0000:00:1c.0: setting latency timer to 64
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447241] pci 0000:00:1e.0: setting latency timer to 64
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447244] bus: 00 index 0 io port: [0, ffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447246] bus: 00 index 1 mmio: [0, ffffffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447248] bus: 01 index 0 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447250] bus: 01 index 1 mmio: [dfc00000, dfcfffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447252] bus: 01 index 2 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447253] bus: 01 index 3 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447255] bus: 02 index 0 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447257] bus: 02 index 1 mmio: [dfb00000, dfbfffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447259] bus: 02 index 2 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447261] bus: 02 index 3 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447262] bus: 03 index 0 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447264] bus: 03 index 1 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447266] bus: 03 index 2 mmio: [0, 0]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447267] bus: 03 index 3 io port: [0, ffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447269] bus: 03 index 4 mmio: [0, ffffffff]
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.447278] NET: Registered protocol family 2
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.460106] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.460336] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.460728] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.460993] TCP: Hash tables configured (established 131072 bind 65536)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.460997] TCP reno registered
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.468180] NET: Registered protocol family 1
Aug 17 16:42:33 sugarbackup-desktop kernel: [    1.468290] checking if image is initramfs... it is
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.091293] Freeing initrd memory: 8007k freed
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.091615] Simple Boot Flag at 0x7a set to 0x1
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.092361] audit: initializing netlink socket (disabled)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.092381] type=2000 audit(1250523710.092:1): initialized
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.097725] highmem bounce pool size: 64 pages
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.097731] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.099833] VFS: Disk quotas dquot_6.5.1
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.099911] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100007] msgmni has been set to 1743
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100122] io scheduler noop registered
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100124] io scheduler anticipatory registered
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100127] io scheduler deadline registered
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100137] io scheduler cfq registered (default)
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100152] pci 0000:00:02.0: Boot video device
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100330] pcieport-driver 0000:00:01.0: setting latency timer to 64
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100365] pcieport-driver 0000:00:01.0: found MSI capability
Aug 17 16:42:33 sugarbackup-desktop kernel: [    2.100393] pci_express 0000:00:01.0:pcie00: allocate port service
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100433] pci_express 0000:00:01.0:pcie03: allocate port service
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100512] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100543] pcieport-driver 0000:00:1c.0: found MSI capability
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100575] pci_express 0000:00:1c.0:pcie00: allocate port service
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100613] pci_express 0000:00:1c.0:pcie02: allocate port service
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100649] pci_express 0000:00:1c.0:pcie03: allocate port service
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.100937] isapnp: Scanning for PnP cards...
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.453754] isapnp: No Plug & Play device found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.483572] hpet_resources: 0xfed00000 is busy
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.483622] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.483746] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.484452] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.486131] brd: module loaded
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.486196] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.486360] PNP: No PS/2 controller found. Probing ports directly.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.488916] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.488921] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489175] mice: PS/2 mouse device common for all mice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489294] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489316] rtc0: alarms up to one day, hpet irqs
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489431] EISA: Probing bus 0 at eisa.0
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489457] EISA: Detected 0 cards.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489461] cpuidle: using governor ladder
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489463] cpuidle: using governor menu
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489939] TCP cubic registered
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.489968] Using IPI No-Shortcut mode
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490142] registered taskstats version 1
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490267]   Magic number: 5:14:690
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490331] mem mem: hash matches
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490365] rtc_cmos 00:05: setting system clock to 2009-08-17 15:41:51 UTC (1250523711)
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490368] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490370] EDD information not available.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490553] Freeing unused kernel memory: 424k freed
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490588] Write protecting the kernel text: 2576k
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.490613] Write protecting the kernel read-only data: 936k
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.652386] fuse init (API version 7.9)
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.692427] processor ACPI0007:00: registered as cooling_device0
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.692490] processor ACPI0007:01: registered as cooling_device1
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.944274] usbcore: registered new interface driver usbfs
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.944299] usbcore: registered new interface driver hub
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.945020] usbcore: registered new device driver usb
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952558] USB Universal Host Controller Interface driver v3.0
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952612] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952621] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952625] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952670] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952703] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952839] usb usb1: configuration #1 chosen from 1 choice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952870] hub 1-0:1.0: USB hub found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.952880] hub 1-0:1.0: 2 ports detected
Aug 17 16:42:34 sugarbackup-desktop kernel: [    2.995444] No dock devices found.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.022249] SCSI subsystem initialized
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.037934] libata version 3.00 loaded.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056499] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056509] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056513] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056536] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056565] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056650] usb usb2: configuration #1 chosen from 1 choice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056675] hub 2-0:1.0: USB hub found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.056681] hub 2-0:1.0: 2 ports detected
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160484] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160493] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160496] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160520] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160550] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160633] usb usb3: configuration #1 chosen from 1 choice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160658] hub 3-0:1.0: USB hub found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.160665] hub 3-0:1.0: 2 ports detected
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368273] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368282] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368286] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368310] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368340] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368427] usb usb4: configuration #1 chosen from 1 choice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368452] hub 4-0:1.0: USB hub found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.368459] hub 4-0:1.0: 2 ports detected
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.472611] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.472626] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.472629] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.472659] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.476572] ehci_hcd 0000:00:1d.7: debug port 1
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.476579] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.476588] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xff980800
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.480274] usb 3-1: new low speed USB device using uhci_hcd and address 2
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.496026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.496181] usb usb5: configuration #1 chosen from 1 choice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.496209] hub 5-0:1.0: USB hub found
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.496217] hub 5-0:1.0: 8 ports detected
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.552060] hub 3-0:1.0: unable to enumerate USB device on port 1
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700278] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700308] pata_acpi 0000:00:1f.1: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700320] pata_acpi 0000:00:1f.1: PCI INT A disabled
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700351] pata_acpi 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700369] pata_acpi 0000:00:1f.2: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700377] pata_acpi 0000:00:1f.2: PCI INT C disabled
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700393] tg3.c:v3.94 (August 14, 2008)
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700401] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:34 sugarbackup-desktop kernel: [    3.700407] tg3 0000:02:00.0: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.112056] usb 3-1: new low speed USB device using uhci_hcd and address 3
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.228620] eth0: Tigon3 [partno(BCM95784M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:21:9b:72:90:ac
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.228623] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.228626] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.235427] ata_piix 0000:00:1f.1: version 2.12
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.235438] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.235476] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.235991] scsi0 : ata_piix
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236099] scsi1 : ata_piix
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236138] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236141] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236171] ata1: port disabled. ignoring.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236199] ata2: port disabled. ignoring.
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236218] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.236222] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.280739] usb 3-1: configuration #1 chosen from 1 choice
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.392046] ata_piix 0000:00:1f.2: setting latency timer to 64
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.392130] scsi2 : ata_piix
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.392449] scsi3 : ata_piix
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.392489] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfec0 irq 20
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.392492] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfec8 irq 20
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.520031] usb 3-2: new low speed USB device using uhci_hcd and address 4
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.589682] ata3.00: ATA-7: ST3160815AS, 4.ADA, max UDMA/133
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.589688] ata3.00: 312500000 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.656322] ata3.00: configured for UDMA/133
Aug 17 16:42:34 sugarbackup-desktop kernel: [    4.694982] usb 3-2: configuration #1 chosen from 1 choice
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.697821] usbcore: registered new interface driver hiddev
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.710863] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input1
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.713736] input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-1
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.728897] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input2
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.729137] input,hidraw1: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.2-2
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.729158] usbcore: registered new interface driver usbhid
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.729161] usbhid: v2.6:USB HID core driver
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.812188] ata4.01: NODEV after polling detection
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.836207] ata4.00: ATAPI: PBDS CD-RW/DVD-ROM DH-48C2S, ND12, max UDMA/100
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.868211] ata4.00: configured for UDMA/100
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.868326] scsi 2:0:0:0: Direct-Access     ATA      ST3160815AS      4.AD PQ: 0 ANSI: 5
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.869592] scsi 3:0:0:0: CD-ROM            PBDS     CDRWDVD DH-48C2S ND12 PQ: 0 ANSI: 5
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.876411] scsi 2:0:0:0: Attached scsi generic sg0 type 0
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.876446] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.893205] Driver 'sr' needs updating - please use bus_type methods
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.902890] Driver 'sd' needs updating - please use bus_type methods
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.902986] sd 2:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903002] sd 2:0:0:0: [sda] Write Protect is off
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903004] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903029] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903093] sd 2:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903107] sd 2:0:0:0: [sda] Write Protect is off
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903109] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903134] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.903137]  sda:sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.904698] Uniform CD-ROM driver Revision: 3.20
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.904822] sr 3:0:0:0: Attached scsi CD-ROM sr0
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.920874]  sda1 sda2 < sda5 >
Aug 17 16:42:35 sugarbackup-desktop kernel: [    4.945503] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 17 16:42:35 sugarbackup-desktop kernel: [    5.212133] PM: Starting manual resume from disk
Aug 17 16:42:35 sugarbackup-desktop kernel: [    5.212137] PM: Resume from partition 8:5
Aug 17 16:42:35 sugarbackup-desktop kernel: [    5.212138] PM: Checking hibernation image.
Aug 17 16:42:35 sugarbackup-desktop kernel: [    5.212302] PM: Resume from disk failed.
Aug 17 16:42:35 sugarbackup-desktop kernel: [    5.273228] kjournald starting.  Commit interval 5 seconds
Aug 17 16:42:35 sugarbackup-desktop kernel: [    5.273256] EXT3-fs: mounted filesystem with ordered data mode.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.206536] udevd version 124 started
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.557625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.603748] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.660716] Linux agpgart interface v0.103
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.677894] intel_rng: Firmware space is locked read-only. If you can't or
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.677896] intel_rng: don't want to disable this in firmware setup, and if
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.677897] intel_rng: you are certain that your system has a functional
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.677898] intel_rng: RNG, try using the 'no_fwh_detect' option.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.729700] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.748038] ACPI: Power Button (FF) [PWRF]
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.748130] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.756836] agpgart-intel 0000:00:00.0: Intel G33 Chipset
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.757114] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.771208] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.784040] ACPI: Power Button (CM) [VBTN]
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.821682] iTCO_vendor_support: vendor-support=0
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.896655] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.896724] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.896735] iTCO_wdt: No card detected
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.996979] parport_pc 00:06: reported by Plug and Play ACPI
Aug 17 16:42:35 sugarbackup-desktop kernel: [   10.997034] parport0: PC-style at 0x378 (0x77, irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Aug 17 16:42:35 sugarbackup-desktop kernel: [   11.241425] input: PC Speaker as /devices/platform/pcspkr/input/input5
Aug 17 16:42:35 sugarbackup-desktop kernel: [   11.447009] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug 17 16:42:35 sugarbackup-desktop kernel: [   11.613920] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:35 sugarbackup-desktop kernel: [   11.613948] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 17 16:42:35 sugarbackup-desktop kernel: [   13.147293] lp0: using parport0 (interrupt-driven).
Aug 17 16:42:35 sugarbackup-desktop kernel: [   13.253280] Adding 6032368k swap on /dev/sda5.  Priority:-1 extents:1 across:6032368k
Aug 17 16:42:35 sugarbackup-desktop kernel: [   13.812694] EXT3 FS on sda1, internal journal
Aug 17 16:42:35 sugarbackup-desktop kernel: [   14.746792] type=1505 audit(1250523723.688:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3919
Aug 17 16:42:35 sugarbackup-desktop kernel: [   14.900244] type=1505 audit(1250523723.844:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3924
Aug 17 16:42:35 sugarbackup-desktop kernel: [   14.900422] type=1505 audit(1250523723.844:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3924
Aug 17 16:42:35 sugarbackup-desktop kernel: [   14.952071] type=1505 audit(1250523723.896:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3928
Aug 17 16:42:35 sugarbackup-desktop kernel: [   15.064725] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 17 16:42:35 sugarbackup-desktop kernel: [   15.632980] RPC: Registered udp transport module.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   15.632983] RPC: Registered tcp transport module.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   16.843218] tg3: eth0: Link is up at 100 Mbps, full duplex.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   16.843221] tg3: eth0: Flow control is on for TX and on for RX.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   18.162540] NET: Registered protocol family 10
Aug 17 16:42:35 sugarbackup-desktop kernel: [   18.163092] lo: Disabled Privacy Extensions
Aug 17 16:42:35 sugarbackup-desktop kernel: [   18.993490] ACPI: WMI: Mapper loaded
Aug 17 16:42:35 sugarbackup-desktop kernel: [   19.916721] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Aug 17 16:42:35 sugarbackup-desktop kernel: [   22.458137] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 17 16:42:35 sugarbackup-desktop kernel: [   22.458142] apm: disabled - APM is not SMP safe.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   22.682973] ppdev: user-space parallel port driver
Aug 17 16:42:35 sugarbackup-desktop kernel: [   23.491547] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
Aug 17 16:42:35 sugarbackup-desktop kernel: [   23.655034] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Aug 17 16:42:35 sugarbackup-desktop kernel: [   23.665044] NFSD: starting 90-second grace period
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.267724] Bluetooth: Core ver 2.13
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.268462] NET: Registered protocol family 31
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.268468] Bluetooth: HCI device and connection manager initialized
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.268472] Bluetooth: HCI socket layer initialized
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.657414] Bluetooth: L2CAP ver 2.11
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.657419] Bluetooth: L2CAP socket layer initialized
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.668142] Bluetooth: RFCOMM socket layer initialized
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.668155] Bluetooth: RFCOMM TTY layer initialized
Aug 17 16:42:35 sugarbackup-desktop kernel: [   28.668157] Bluetooth: RFCOMM ver 1.10
Aug 17 16:42:35 sugarbackup-desktop kernel: [   29.152015] eth0: no IPv6 routers present
Aug 17 16:42:35 sugarbackup-desktop kernel: [   31.862082] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 17 16:42:35 sugarbackup-desktop kernel: [   31.862088] Bluetooth: BNEP filters: protocol multicast
Aug 17 16:42:35 sugarbackup-desktop kernel: [   31.902067] Bridge firewalling registered
Aug 17 16:42:35 sugarbackup-desktop kernel: [   31.902253] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Aug 17 16:42:35 sugarbackup-desktop kernel: [   33.151551] [drm] Initialized drm 1.1.0 20060810
Aug 17 16:42:35 sugarbackup-desktop kernel: [   33.182678] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 16:42:35 sugarbackup-desktop kernel: [   33.182686] pci 0000:00:02.0: setting latency timer to 64
Aug 17 16:42:35 sugarbackup-desktop kernel: [   33.182814] [drm] Initialized i915 1.6.0 20060119 on minor 0
Aug 17 16:42:35 sugarbackup-desktop kernel: [   33.338158] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 17 16:42:35 sugarbackup-desktop kernel: [   33.749907] set status page addr 0x00033000
Aug 17 16:42:35 sugarbackup-desktop kernel: [   40.745698] Bluetooth: SCO (Voice Link) ver 0.6

---

