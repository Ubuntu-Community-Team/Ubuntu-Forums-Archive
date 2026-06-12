---
title: "Computer boots alone at certain time every night (intrepid Ibex)"
date: 2010-01-16
forum: General Help
---

### Post by Maju on 2010-01-16
Hello, I recently had the (dubiously good) idea of upgrading my Hardy Heron to Intrepid Ibex (actually I hoped to get directly into a more advanced version but guess not). Since then I have a very strange issue (I have searched and found nothing alike except [this thread]("http://ubuntuforums.org/showthread.php?t=765401&highlight=starts+alone")):

At 1:00 the computer starts on its own, with the side effects of wasting electricity and waking me up. After taking off schedulers and other stuff that looked like unnecessary (based on searchs in this forum), it still does it, producing the following logs:

```
Jan 17 01:00:39 euskaltel sudo:     root : unable to resolve host euskaltel
Jan 17 01:00:39 euskaltel sudo:     root : TTY=console ; PWD=/ ; USER=root ; COMMAND=/sbin/insmod -f /lib/modules/2.6.27-16-generic/kernel/drivers/char/agrmodem.ko
Jan 17 01:00:39 euskaltel sudo:     root : unable to resolve host euskaltel
Jan 17 01:00:39 euskaltel sudo:     root : TTY=console ; PWD=/ ; USER=root ; COMMAND=/sbin/insmod -f /lib/modules/2.6.27-16-generic/kernel/drivers/char/agrserial.ko
Jan 17 01:10:01 euskaltel CRON[5561]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:10:05 euskaltel CRON[5561]: pam_unix(cron:session): session closed for user root
Jan 17 01:17:01 euskaltel CRON[5645]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:17:01 euskaltel CRON[5645]: pam_unix(cron:session): session closed for user root
Jan 17 01:20:01 euskaltel CRON[5689]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:20:02 euskaltel CRON[5689]: pam_unix(cron:session): session closed for user root
Jan 17 01:30:01 euskaltel CRON[5772]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:30:02 euskaltel CRON[5772]: pam_unix(cron:session): session closed for user root
Jan 17 01:40:01 euskaltel CRON[5855]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:40:01 euskaltel CRON[5855]: pam_unix(cron:session): session closed for user root
Jan 17 01:50:01 euskaltel CRON[5938]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:50:01 euskaltel CRON[5938]: pam_unix(cron:session): session closed for user root
Jan 17 02:00:01 euskaltel CRON[6021]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 02:00:02 euskaltel CRON[6021]: pam_unix(cron:session): session closed for user root
Jan 17 02:10:01 euskaltel CRON[6104]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 02:10:02 euskaltel CRON[6104]: pam_unix(cron:session): session closed for user root
Jan 17 02:17:01 euskaltel CRON[6187]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 02:17:01 euskaltel CRON[6187]: pam_unix(cron:session): session closed for user root
```

```
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped root privileges.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: avahi-daemon 0.6.23 starting up.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully called chroot().
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped remaining capabilities.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: No service file found in /etc/avahi/services.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Network interface enumeration completed.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Server startup complete. Host name is euskaltel.local. Local service cookie is 3919910173.
Jan 17 01:00:50 euskaltel acpid: client connected from 5167[111:123] 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 104 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 135 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_keys: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:52 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:53 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:58 euskaltel dhclient: DHCPREQUEST of 85.84.234.186 on eth2 to 255.255.255.255 port 67
Jan 17 01:00:58 euskaltel dhclient: DHCPACK of 85.84.234.186 from 10.77.128.1
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel dhclient: bound to 85.84.234.186 -- renewal in 35752 seconds.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:01:00 euskaltel ntpdate[5551]: adjust time server 91.189.94.4 offset -0.147056 sec
Jan 17 01:01:01 euskaltel avahi-daemon[4720]: Registering new address record for fe80::218:68ff:fe0a:5975 on eth2.*.
Jan 17 02:18:28 euskaltel init: tty4 main process (4296) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty5 main process (4297) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty2 main process (4304) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty3 main process (4305) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty6 main process (4306) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty1 main process (5457) killed by TERM signal
```

This last is obviously my manually turning it off. 

```
Jan 17 01:00:38 euskaltel kernel: [    0.000000] kernel direct mapping tables up to 37ee0000 @ 10000-16000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] On node 0 totalpages: 228975
Jan 17 01:00:38 euskaltel kernel: [    0.000000] free_area_init_node: node 0, pgdat c048e700, node_mem_map c1000240
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal zone: 223014 pages, LIFO batch:31
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jan 17 01:00:38 euskaltel kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jan 17 01:00:38 euskaltel kernel: [    0.004000] hpet clockevent registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] CPU0 attaching NULL sched-domain.
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: EC: Look up EC in DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.389538] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
Jan 17 01:00:38 euskaltel kernel: [    0.389570] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389580] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389584] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
Jan 17 01:00:38 euskaltel kernel: [    0.389652] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.389676] pci 0000:00:02.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389678] pci 0000:00:02.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389701] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
Jan 17 01:00:38 euskaltel kernel: [    0.389731] pci 0000:00:02.1: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389732] pci 0000:00:02.1: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389790] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
Jan 17 01:00:38 euskaltel kernel: [    0.389850] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
Jan 17 01:00:38 euskaltel kernel: [    0.389884] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389888] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
Jan 17 01:00:38 euskaltel kernel: [    0.389914] pci 0000:00:07.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389916] pci 0000:00:07.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389937] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
Jan 17 01:00:38 euskaltel kernel: [    0.389941] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
Jan 17 01:00:38 euskaltel kernel: [    0.389944] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
Jan 17 01:00:38 euskaltel kernel: [    0.389948] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
Jan 17 01:00:38 euskaltel kernel: [    0.389951] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
Jan 17 01:00:38 euskaltel kernel: [    0.389955] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389985] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
Jan 17 01:00:38 euskaltel kernel: [    0.389989] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
Jan 17 01:00:38 euskaltel kernel: [    0.389992] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
Jan 17 01:00:38 euskaltel kernel: [    0.389996] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
Jan 17 01:00:38 euskaltel kernel: [    0.389999] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
Jan 17 01:00:38 euskaltel kernel: [    0.390003] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390129] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390134] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390139] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390144] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390251] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390254] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390257] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390290] PCI: bridge 0000:00:09.0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.390293] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390296] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390329] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390331] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390335] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390367] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390369] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390381] bus 00 -> node 0
Jan 17 01:00:38 euskaltel kernel: [    0.390389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.390753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.460042] Switched to high resolution mode on CPU 0
Jan 17 01:00:38 euskaltel kernel: [    0.493565] pci 0000:00:04.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493570] pci 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493575] pci 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493579] pci 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136173] pci 0000:00:0d.0: Boot video device
Jan 17 01:00:38 euskaltel kernel: [    1.136260] pcieport-driver 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136300] pci_express 0000:00:09.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136332] pci_express 0000:00:09.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136386] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136422] pci_express 0000:00:0b.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136451] pci_express 0000:00:0b.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136504] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136539] pci_express 0000:00:0c.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136569] pci_express 0000:00:0c.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.519451] hpet_resources: 0xfeff0000 is busy
Jan 17 01:00:38 euskaltel kernel: [    2.810196] forcedeth 0000:00:07.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    2.814686] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 17 01:00:38 euskaltel kernel: [    2.831542] libata version 3.00 loaded.
Jan 17 01:00:38 euskaltel kernel: [    3.328984] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592921] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592970] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 17 01:00:38 euskaltel kernel: [    3.817083] sata_nv 0000:00:08.0: version 3.5
Jan 17 01:00:38 euskaltel kernel: [    3.817543] sata_nv 0000:00:08.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    4.633148] sata_nv 0000:00:08.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.325753] usb-storage: device found at 3
Jan 17 01:00:38 euskaltel kernel: [    5.325754] usb-storage: waiting for device to settle before scanning
Jan 17 01:00:38 euskaltel kernel: [    5.449816] pata_amd 0000:00:06.0: version 0.3.10
Jan 17 01:00:38 euskaltel kernel: [    5.449860] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.614957] ata6: port disabled. ignoring.
Jan 17 01:00:38 euskaltel kernel: [    5.656173] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656264] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.717972] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 17 01:00:38 euskaltel kernel: [    5.869219] PM: Resume from partition 8:5
Jan 17 01:00:38 euskaltel kernel: [    5.869221] PM: Checking hibernation image.
Jan 17 01:00:38 euskaltel kernel: [    5.869321] PM: Resume from disk failed.
Jan 17 01:00:38 euskaltel kernel: [   10.324166] usb-storage: device scan complete
Jan 17 01:00:38 euskaltel kernel: [   13.984631] HDA Intel 0000:00:05.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   16.015105] nvidia 0000:00:0d.0: setting latency timer to 64
Jan 17 01:01:10 euskaltel kernel: [   53.888014] eth2: no IPv6 routers present
```

```
Jan 17 01:00:38 euskaltel kernel: Inspecting /boot/System.map-2.6.27-16-generic
Jan 17 01:00:38 euskaltel kernel: Cannot find map file.
Jan 17 01:00:38 euskaltel kernel: Loaded 67477 symbols from 83 modules.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Linux version 2.6.27-16-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Dec 1 17:56:54 UTC 2009 (Ubuntu 2.6.27-16.44-generic)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] DMI 2.5 present.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] kernel direct mapping tables up to 37ee0000 @ 10000-16000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] RAMDISK: 37709000 - 37ecf0f3
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDT 37EE3000, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACP 37EE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: DSDT 37EE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACS 37EE0000, 0040
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: SSDT 37EEA000, 0115 (r1 PTLTD  POWERNOW        1  LTP        1)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET 37EEA140, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA       98)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: MCFG 37EEA180, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: APIC 37EE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 0MB HIGHMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 894MB LOWMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   mapped low ram: 0 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   low ram: 00000000 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   bootmap 00012000 - 00018fdc
Jan 17 01:00:38 euskaltel kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ee0000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #4 [0037709000 - 0037ecf0f3]          RAMDISK ==> [0037709000 - 0037ecf0f3]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Zone PFN ranges:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal   0x00001000 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   HighMem  0x00037ee0 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Movable zone start PFN for each node
Jan 17 01:00:38 euskaltel kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000100 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] On node 0 totalpages: 228975
Jan 17 01:00:38 euskaltel kernel: [    0.000000] free_area_init_node: node 0, pgdat c048e700, node_mem_map c1000240
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal zone: 223014 pages, LIFO batch:31
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 17 01:00:38 euskaltel kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jan 17 01:00:38 euskaltel kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226961
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Kernel command line: root=UUID=f825bb92-55a9-4133-bbf2-a7298808771e ro quiet splash 
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing CPU#0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: using PIT calibration value
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected 2210.001 MHz processor.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Console: colour VGA+ 80x25
Jan 17 01:00:38 euskaltel kernel: [    0.004000] console [tty0] enabled
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Memory: 893820k/916352k available (2585k kernel code, 21936k reserved, 1164k data, 428k init, 0k highmem)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] virtual kernel memory layout:
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf7ee0000   ( 894 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .data : 0xc03864c8 - 0xc04a9680   (1164 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .text : 0xc0100000 - 0xc03864c8   (2585 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 17 01:00:38 euskaltel kernel: [    0.004000] hpet clockevent registered
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.00 BogoMIPS (lpj=8840004)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Security Framework initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SELinux:  Disabled at boot.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] AppArmor: AppArmor initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Mount-cache hash table entries: 512
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys ns
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys cpuacct
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys memory
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] using C1E aware idle routine
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking 'hlt' instruction... OK.
Jan 17 01:00:38 euskaltel kernel: [    0.016301] SMP alternatives: switching to UP code
Jan 17 01:00:38 euskaltel kernel: [    0.020009] ACPI: Core revision 20080609
Jan 17 01:00:38 euskaltel kernel: [    0.022070] ACPI: Checking initramfs for custom DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.328299] ENABLING IO-APIC IRQs
Jan 17 01:00:38 euskaltel kernel: [    0.328524] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 17 01:00:38 euskaltel kernel: [    0.370956] CPU0: AMD Athlon(tm) Processor LE-1600 stepping 03
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Brought up 1 CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Total of 1 processors activated (4420.00 BogoMIPS).
Jan 17 01:00:38 euskaltel kernel: [    0.372023] CPU0 attaching NULL sched-domain.
Jan 17 01:00:38 euskaltel kernel: [    0.372023] net_namespace: 840 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Booting paravirtualized kernel on bare hardware
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Time:  0:00:17  Date: 01/17/10
Jan 17 01:00:38 euskaltel kernel: [    0.372023] NET: Registered protocol family 16
Jan 17 01:00:38 euskaltel kernel: [    0.372023] EISA bus registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: bus type pci registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG area at f0000000 reserved in E820
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using MMCONFIG for extended config space
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using configuration type 1 for base access
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: EC: Look up EC in DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.379182] ACPI: Interpreter enabled
Jan 17 01:00:38 euskaltel kernel: [    0.379185] ACPI: (supports S0 S3 S4 S5)
Jan 17 01:00:38 euskaltel kernel: [    0.379199] ACPI: Using IOAPIC for interrupt routing
Jan 17 01:00:38 euskaltel kernel: [    0.389348] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 17 01:00:38 euskaltel kernel: [    0.389538] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
Jan 17 01:00:38 euskaltel kernel: [    0.389570] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389580] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389584] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
Jan 17 01:00:38 euskaltel kernel: [    0.389607] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389612] pci 0000:00:01.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389652] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.389676] pci 0000:00:02.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389678] pci 0000:00:02.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389680] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389683] pci 0000:00:02.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389701] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
Jan 17 01:00:38 euskaltel kernel: [    0.389731] pci 0000:00:02.1: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389732] pci 0000:00:02.1: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389734] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389738] pci 0000:00:02.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389790] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
Jan 17 01:00:38 euskaltel kernel: [    0.389820] pci 0000:00:05.0: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389823] pci 0000:00:05.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389850] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
Jan 17 01:00:38 euskaltel kernel: [    0.389884] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389888] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
Jan 17 01:00:38 euskaltel kernel: [    0.389914] pci 0000:00:07.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389916] pci 0000:00:07.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389918] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389922] pci 0000:00:07.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389937] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
Jan 17 01:00:38 euskaltel kernel: [    0.389941] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
Jan 17 01:00:38 euskaltel kernel: [    0.389944] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
Jan 17 01:00:38 euskaltel kernel: [    0.389948] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
Jan 17 01:00:38 euskaltel kernel: [    0.389951] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
Jan 17 01:00:38 euskaltel kernel: [    0.389955] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389985] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
Jan 17 01:00:38 euskaltel kernel: [    0.389989] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
Jan 17 01:00:38 euskaltel kernel: [    0.389992] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
Jan 17 01:00:38 euskaltel kernel: [    0.389996] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
Jan 17 01:00:38 euskaltel kernel: [    0.389999] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
Jan 17 01:00:38 euskaltel kernel: [    0.390003] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390052] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390055] pci 0000:00:09.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390084] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390087] pci 0000:00:0b.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390115] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390118] pci 0000:00:0c.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390129] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390134] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390139] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390144] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390248] pci 0000:00:04.0: transparent bridge
Jan 17 01:00:38 euskaltel kernel: [    0.390251] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390254] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390257] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390290] PCI: bridge 0000:00:09.0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.390293] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390296] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390329] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390331] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390335] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390367] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390369] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390381] bus 00 -> node 0
Jan 17 01:00:38 euskaltel kernel: [    0.390389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.390753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.442082] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442278] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442472] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442666] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442860] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443054] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443248] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443442] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443639] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.443832] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444034] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444235] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Jan 17 01:00:38 euskaltel kernel: [    0.444430] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444624] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444820] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445019] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445214] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.445410] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445609] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445853] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446091] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446327] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446563] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446799] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447036] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447272] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447508] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447744] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.447984] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448231] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448468] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.448706] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448943] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449180] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449417] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449655] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449892] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450128] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450292] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 17 01:00:38 euskaltel kernel: [    0.450319] pnp: PnP ACPI init
Jan 17 01:00:38 euskaltel kernel: [    0.450325] ACPI: bus type pnp registered
Jan 17 01:00:38 euskaltel kernel: [    0.455979] pnp: PnP ACPI: found 12 devices
Jan 17 01:00:38 euskaltel kernel: [    0.455981] ACPI: ACPI bus type pnp unregistered
Jan 17 01:00:38 euskaltel kernel: [    0.455983] PnPBIOS: Disabled by ACPI PNP
Jan 17 01:00:38 euskaltel kernel: [    0.456252] PCI: Using ACPI for IRQ routing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 8
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 20
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel: Initializing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  domain hash size = 128
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  unlabeled traffic allowed by default
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: 3 32-bit timers, 25000000 Hz
Jan 17 01:00:38 euskaltel kernel: [    0.457996] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.457998]    actual entries 65620
Jan 17 01:00:38 euskaltel kernel: [    0.458152] AppArmor: AppArmor Filesystem Enabled
Jan 17 01:00:38 euskaltel kernel: [    0.458176] ACPI: RTC can wake from S4
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1000-0x107f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1400-0x147f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1800-0x187f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2000-0x207f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2080-0x20ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x295-0x314 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x38000000-0x3fffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.460042] Switched to high resolution mode on CPU 0
Jan 17 01:00:38 euskaltel kernel: [    0.493510] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Jan 17 01:00:38 euskaltel kernel: [    0.493513] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
Jan 17 01:00:38 euskaltel kernel: [    0.493516] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493520] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jan 17 01:00:38 euskaltel kernel: [    0.493524] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Jan 17 01:00:38 euskaltel kernel: [    0.493527] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Jan 17 01:00:38 euskaltel kernel: [    0.493530] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
Jan 17 01:00:38 euskaltel kernel: [    0.493533] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493536] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Jan 17 01:00:38 euskaltel kernel: [    0.493539] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Jan 17 01:00:38 euskaltel kernel: [    0.493542] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493545] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493548] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Jan 17 01:00:38 euskaltel kernel: [    0.493551] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Jan 17 01:00:38 euskaltel kernel: [    0.493554] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Jan 17 01:00:38 euskaltel kernel: [    0.493557] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493565] pci 0000:00:04.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493570] pci 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493575] pci 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493579] pci 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493582] bus: 00 index 0 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493584] bus: 00 index 1 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493586] bus: 01 index 0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.493588] bus: 01 index 1 mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493590] bus: 01 index 2 mmio: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493592] bus: 01 index 3 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493594] bus: 01 index 4 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493596] bus: 02 index 0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.493598] bus: 02 index 1 mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493600] bus: 02 index 2 mmio: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493602] bus: 02 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493604] bus: 03 index 0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493606] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493608] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493610] bus: 03 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493612] bus: 04 index 0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493614] bus: 04 index 1 mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493616] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493617] bus: 04 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493627] NET: Registered protocol family 2
Jan 17 01:00:38 euskaltel kernel: [    0.493763] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494036] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494820] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.495192] TCP: Hash tables configured (established 131072 bind 65536)
Jan 17 01:00:38 euskaltel kernel: [    0.495194] TCP reno registered
Jan 17 01:00:38 euskaltel kernel: [    0.495327] NET: Registered protocol family 1
Jan 17 01:00:38 euskaltel kernel: [    0.495434] checking if image is initramfs... it is
Jan 17 01:00:38 euskaltel kernel: [    1.115818] Freeing initrd memory: 7960k freed
Jan 17 01:00:38 euskaltel kernel: [    1.116448] audit: initializing netlink socket (disabled)
Jan 17 01:00:38 euskaltel kernel: [    1.116461] type=2000 audit(1263686417.116:1): initialized
Jan 17 01:00:38 euskaltel kernel: [    1.121466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 17 01:00:38 euskaltel kernel: [    1.123323] VFS: Disk quotas dquot_6.5.1
Jan 17 01:00:38 euskaltel kernel: [    1.123393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 17 01:00:38 euskaltel kernel: [    1.123487] msgmni has been set to 1761
Jan 17 01:00:38 euskaltel kernel: [    1.123588] io scheduler noop registered
Jan 17 01:00:38 euskaltel kernel: [    1.123590] io scheduler anticipatory registered
Jan 17 01:00:38 euskaltel kernel: [    1.123592] io scheduler deadline registered
Jan 17 01:00:38 euskaltel kernel: [    1.123602] io scheduler cfq registered (default)
Jan 17 01:00:38 euskaltel kernel: [    1.123635] pci 0000:00:00.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136045] pci 0000:00:04.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136061] pci 0000:00:05.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136087] pci 0000:00:07.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136101] pci 0000:00:08.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136115] pci 0000:00:08.1: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136130] pci 0000:00:09.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136144] pci 0000:00:0b.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136159] pci 0000:00:0c.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136173] pci 0000:00:0d.0: Boot video device
Jan 17 01:00:38 euskaltel kernel: [    1.136260] pcieport-driver 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136282] pcieport-driver 0000:00:09.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136300] pci_express 0000:00:09.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136332] pci_express 0000:00:09.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136386] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136407] pcieport-driver 0000:00:0b.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136422] pci_express 0000:00:0b.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136451] pci_express 0000:00:0b.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136504] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136524] pcieport-driver 0000:00:0c.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136539] pci_express 0000:00:0c.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136569] pci_express 0000:00:0c.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136783] isapnp: Scanning for PnP cards...
Jan 17 01:00:38 euskaltel kernel: [    1.489432] isapnp: No Plug & Play device found
Jan 17 01:00:38 euskaltel kernel: [    1.519451] hpet_resources: 0xfeff0000 is busy
Jan 17 01:00:38 euskaltel kernel: [    1.519522] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 17 01:00:38 euskaltel kernel: [    1.521642] brd: module loaded
Jan 17 01:00:38 euskaltel kernel: [    1.521708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 17 01:00:38 euskaltel kernel: [    1.521800] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 17 01:00:38 euskaltel kernel: [    1.522162] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 17 01:00:38 euskaltel kernel: [    1.522166] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 17 01:00:38 euskaltel kernel: [    1.522464] mice: PS/2 mouse device common for all mice
Jan 17 01:00:38 euskaltel kernel: [    1.522576] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jan 17 01:00:38 euskaltel kernel: [    1.522610] rtc0: alarms up to one year, y3k, hpet irqs
Jan 17 01:00:38 euskaltel kernel: [    1.522699] EISA: Probing bus 0 at eisa.0
Jan 17 01:00:38 euskaltel kernel: [    1.522704] Cannot allocate resource for EISA slot 1
Jan 17 01:00:38 euskaltel kernel: [    1.522707] Cannot allocate resource for EISA slot 2
Jan 17 01:00:38 euskaltel kernel: [    1.522720] Cannot allocate resource for EISA slot 8
Jan 17 01:00:38 euskaltel kernel: [    1.522722] EISA: Detected 0 cards.
Jan 17 01:00:38 euskaltel kernel: [    1.522725] cpuidle: using governor ladder
Jan 17 01:00:38 euskaltel kernel: [    1.522727] cpuidle: using governor menu
Jan 17 01:00:38 euskaltel kernel: [    1.523155] TCP cubic registered
Jan 17 01:00:38 euskaltel kernel: [    1.523179] Using IPI No-Shortcut mode
Jan 17 01:00:38 euskaltel kernel: [    1.523328] registered taskstats version 1
Jan 17 01:00:38 euskaltel kernel: [    1.523443]   Magic number: 10:203:1
Jan 17 01:00:38 euskaltel kernel: [    1.523450] tty ttye9: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523461] tty ttybc: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523652] rtc_cmos 00:05: setting system clock to 2010-01-17 00:00:18 UTC (1263686418)
Jan 17 01:00:38 euskaltel kernel: [    1.523655] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 17 01:00:38 euskaltel kernel: [    1.523657] EDD information not available.
Jan 17 01:00:38 euskaltel kernel: [    1.524041] Freeing unused kernel memory: 428k freed
Jan 17 01:00:38 euskaltel kernel: [    1.524109] Write protecting the kernel text: 2588k
Jan 17 01:00:38 euskaltel kernel: [    1.524147] Write protecting the kernel read-only data: 940k
Jan 17 01:00:38 euskaltel kernel: [    1.544813] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 17 01:00:38 euskaltel kernel: [    1.744060] fuse init (API version 7.9)
Jan 17 01:00:38 euskaltel kernel: [    1.862062] fan PNP0C0B:00: registered as cooling_device0
Jan 17 01:00:38 euskaltel kernel: [    1.862067] ACPI: Fan [FAN] (on)
Jan 17 01:00:38 euskaltel kernel: [    1.868784] processor ACPI0007:00: registered as cooling_device1
Jan 17 01:00:38 euskaltel kernel: [    1.870876] ACPI: Expecting a [Reference] package element, found type 0
Jan 17 01:00:38 euskaltel kernel: [    1.871083] thermal LNXTHERM:01: registered as thermal_zone0
Jan 17 01:00:38 euskaltel kernel: [    1.871449] ACPI: Thermal Zone [THRM] (30 C)
Jan 17 01:00:38 euskaltel kernel: [    2.744077] usbcore: registered new interface driver usbfs
Jan 17 01:00:38 euskaltel kernel: [    2.744101] usbcore: registered new interface driver hub
Jan 17 01:00:38 euskaltel kernel: [    2.752175] No dock devices found.
Jan 17 01:00:38 euskaltel kernel: [    2.784050] usbcore: registered new device driver usb
Jan 17 01:00:38 euskaltel kernel: [    2.809697] SCSI subsystem initialized
Jan 17 01:00:38 euskaltel kernel: [    2.809760] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jan 17 01:00:38 euskaltel kernel: [    2.810181] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810191] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810196] forcedeth 0000:00:07.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    2.814686] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 17 01:00:38 euskaltel kernel: [    2.831542] libata version 3.00 loaded.
Jan 17 01:00:38 euskaltel kernel: [    3.328497] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:72:a9:fe:35
Jan 17 01:00:38 euskaltel kernel: [    3.328502] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Jan 17 01:00:38 euskaltel kernel: [    3.328958] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328970] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328984] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.328987] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.329023] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Jan 17 01:00:38 euskaltel kernel: [    3.329045] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Jan 17 01:00:38 euskaltel kernel: [    3.386211] usb usb1: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.386319] hub 1-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.386328] hub 1-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.592901] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592911] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 20 (level, low) -> IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592921] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592923] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.592944] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Jan 17 01:00:38 euskaltel kernel: [    3.592966] ehci_hcd 0000:00:02.1: debug port 1
Jan 17 01:00:38 euskaltel kernel: [    3.592970] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 17 01:00:38 euskaltel kernel: [    3.592984] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
Jan 17 01:00:38 euskaltel kernel: [    3.604016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 17 01:00:38 euskaltel kernel: [    3.604090] usb usb2: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.604113] hub 2-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.604120] hub 2-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.817083] sata_nv 0000:00:08.0: version 3.5
Jan 17 01:00:38 euskaltel kernel: [    3.817493] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817503] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817543] sata_nv 0000:00:08.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.820082] scsi0 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821181] scsi1 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821357] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Jan 17 01:00:38 euskaltel kernel: [    3.821360] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.076014] usb 2-8: new high speed USB device using ehci_hcd and address 3
Jan 17 01:00:38 euskaltel kernel: [    4.608032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    4.616299] ata2.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.616302] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 17 01:00:38 euskaltel kernel: [    4.632527] ata2.00: configured for UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.632609] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    4.633103] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633108] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633148] sata_nv 0000:00:08.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    4.633465] scsi2 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633673] scsi3 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633831] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.633834] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.763877] usb 2-8: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    5.072017] usb 1-2: new full speed USB device using ohci_hcd and address 2
Jan 17 01:00:38 euskaltel kernel: [    5.100033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    5.108119] ata3.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.124122] ata3.00: configured for UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.293649] usb 1-2: configuration #1 chosen from 2 choices
Jan 17 01:00:38 euskaltel kernel: [    5.312194] usbcore: registered new interface driver libusual
Jan 17 01:00:38 euskaltel kernel: [    5.324111] Initializing USB Mass Storage driver...
Jan 17 01:00:38 euskaltel kernel: [    5.325593] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 17 01:00:38 euskaltel kernel: [    5.325675] usbcore: registered new interface driver usb-storage
Jan 17 01:00:38 euskaltel kernel: [    5.325678] USB Mass Storage support registered.
Jan 17 01:00:38 euskaltel kernel: [    5.325753] usb-storage: device found at 3
Jan 17 01:00:38 euskaltel kernel: [    5.325754] usb-storage: waiting for device to settle before scanning
Jan 17 01:00:38 euskaltel kernel: [    5.334886] scsi 1:0:0:0: Attached scsi generic sg0 type 0
Jan 17 01:00:38 euskaltel kernel: [    5.449650] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    5.449776] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Jan 17 01:00:38 euskaltel kernel: [    5.449816] pata_amd 0000:00:06.0: version 0.3.10
Jan 17 01:00:38 euskaltel kernel: [    5.449860] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.450312] scsi5 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.450553] scsi6 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.451328] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 17 01:00:38 euskaltel kernel: [    5.451332] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 17 01:00:38 euskaltel kernel: [    5.614957] ata6: port disabled. ignoring.
Jan 17 01:00:38 euskaltel kernel: [    5.656068] Driver 'sd' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.656157] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656171] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656173] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656192] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656251] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656261] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656264] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656282] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656285]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.679675]  sda1 sda2 < sda5 >
Jan 17 01:00:38 euskaltel kernel: [    5.705190] sd 1:0:0:0: [sda] Attached SCSI disk
Jan 17 01:00:38 euskaltel kernel: [    5.717880] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 17 01:00:38 euskaltel kernel: [    5.717885] Uniform CD-ROM driver Revision: 3.20
Jan 17 01:00:38 euskaltel kernel: [    5.717972] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 17 01:00:38 euskaltel kernel: [    5.869216] PM: Starting manual resume from disk
Jan 17 01:00:38 euskaltel kernel: [    5.869219] PM: Resume from partition 8:5
Jan 17 01:00:38 euskaltel kernel: [    5.869221] PM: Checking hibernation image.
Jan 17 01:00:38 euskaltel kernel: [    5.869321] PM: Resume from disk failed.
Jan 17 01:00:38 euskaltel kernel: [    5.923899] kjournald starting.  Commit interval 5 seconds
Jan 17 01:00:38 euskaltel kernel: [    5.923910] EXT3-fs: mounted filesystem with ordered data mode.
Jan 17 01:00:38 euskaltel kernel: [   10.324166] usb-storage: device scan complete
Jan 17 01:00:38 euskaltel kernel: [   10.330532] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Jan 17 01:00:38 euskaltel kernel: [   10.331710] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 17 01:00:38 euskaltel kernel: [   10.331831] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 17 01:00:38 euskaltel kernel: [   12.116177] udevd version 124 started
Jan 17 01:00:38 euskaltel kernel: [   12.580180] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Jan 17 01:00:38 euskaltel kernel: [   12.580209] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
Jan 17 01:00:38 euskaltel kernel: [   13.024208] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 17 01:00:38 euskaltel kernel: [   13.040031] ACPI: Power Button (FF) [PWRF]
Jan 17 01:00:38 euskaltel kernel: [   13.040103] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Jan 17 01:00:38 euskaltel kernel: [   13.056033] ACPI: Power Button (CM) [PWRB]
Jan 17 01:00:38 euskaltel kernel: [   13.064162] ACPI: WMI: Mapper loaded
Jan 17 01:00:38 euskaltel kernel: [   13.984598] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984604] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984631] HDA Intel 0000:00:05.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   15.208291] eth1: register 'cdc_ether' at usb-0000:00:02.0-2, CDC Ethernet Device, 00:18:68:0a:59:75
Jan 17 01:00:38 euskaltel kernel: [   15.208311] usbcore: registered new interface driver cdc_ether
Jan 17 01:00:38 euskaltel kernel: [   15.366813] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 17 01:00:38 euskaltel kernel: [   15.393091] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 17 01:00:38 euskaltel kernel: [   15.457623] Linux agpgart interface v0.103
Jan 17 01:00:38 euskaltel kernel: [   15.638236] nvidia: module license 'NVIDIA' taints kernel.
Jan 17 01:00:38 euskaltel kernel: [   16.015092] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015098] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015105] nvidia 0000:00:0d.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   16.015355] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
Jan 17 01:00:38 euskaltel kernel: [   16.140880] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jan 17 01:00:38 euskaltel kernel: [   16.823744] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jan 17 01:00:38 euskaltel kernel: [   17.178460] udev: renamed network interface eth1 to eth2
Jan 17 01:00:38 euskaltel kernel: [   18.116894] lp: driver loaded but no devices found
Jan 17 01:00:38 euskaltel kernel: [   18.320383] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
Jan 17 01:00:38 euskaltel kernel: [   18.870393] EXT3 FS on sda1, internal journal
Jan 17 01:00:38 euskaltel kernel: [   20.073620] type=1505 audit(1263686437.081:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4096
Jan 17 01:00:38 euskaltel kernel: [   20.259552] type=1505 audit(1263686437.265:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.259778] type=1505 audit(1263686437.265:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.415348] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 17 01:00:38 euskaltel kernel: [   21.109118] powernow-k8: Found 1 AMD Athlon(tm) Processor LE-1600 processors (1 cpu cores) (version 2.20.00)
Jan 17 01:00:38 euskaltel kernel: [   21.109155] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
Jan 17 01:00:38 euskaltel kernel: [   21.109157] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
Jan 17 01:00:38 euskaltel kernel: [   21.109159] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
Jan 17 01:00:38 euskaltel kernel: [   21.109161] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jan 17 01:00:38 euskaltel kernel: [   21.923180] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 17 01:00:46 euskaltel kernel: [   29.634910] ppdev: user-space parallel port driver
Jan 17 01:00:50 euskaltel kernel: [   33.633134] eth0: no link during initialization.
Jan 17 01:00:51 euskaltel kernel: [   34.500016] Clocksource tsc unstable (delta = -90874311 ns)
Jan 17 01:00:55 euskaltel kernel: [   38.516037] NET: Registered protocol family 17
Jan 17 01:00:59 euskaltel kernel: [   42.926947] NET: Registered protocol family 10
Jan 17 01:00:59 euskaltel kernel: [   42.928576] lo: Disabled Privacy Extensions
Jan 17 01:00:59 euskaltel kernel: [   42.929484] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 17 01:01:10 euskaltel kernel: [   53.888014] eth2: no IPv6 routers present
```

```
Jan 17 01:00:38 euskaltel syslogd 1.5.0#2ubuntu6: restart.
Jan 17 01:00:38 euskaltel kernel: Inspecting /boot/System.map-2.6.27-16-generic
Jan 17 01:00:38 euskaltel kernel: Cannot find map file.
Jan 17 01:00:38 euskaltel kernel: Loaded 67477 symbols from 83 modules.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Linux version 2.6.27-16-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Dec 1 17:56:54 UTC 2009 (Ubuntu 2.6.27-16.44-generic)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] DMI 2.5 present.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] kernel direct mapping tables up to 37ee0000 @ 10000-16000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] RAMDISK: 37709000 - 37ecf0f3
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDT 37EE3000, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACP 37EE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: DSDT 37EE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACS 37EE0000, 0040
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: SSDT 37EEA000, 0115 (r1 PTLTD  POWERNOW        1  LTP        1)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET 37EEA140, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA       98)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: MCFG 37EEA180, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: APIC 37EE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 0MB HIGHMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 894MB LOWMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   mapped low ram: 0 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   low ram: 00000000 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   bootmap 00012000 - 00018fdc
Jan 17 01:00:38 euskaltel kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ee0000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #4 [0037709000 - 0037ecf0f3]          RAMDISK ==> [0037709000 - 0037ecf0f3]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Zone PFN ranges:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal   0x00001000 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   HighMem  0x00037ee0 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Movable zone start PFN for each node
Jan 17 01:00:38 euskaltel kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000100 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] On node 0 totalpages: 228975
Jan 17 01:00:38 euskaltel kernel: [    0.000000] free_area_init_node: node 0, pgdat c048e700, node_mem_map c1000240
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal zone: 223014 pages, LIFO batch:31
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 17 01:00:38 euskaltel kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jan 17 01:00:38 euskaltel kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226961
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Kernel command line: root=UUID=f825bb92-55a9-4133-bbf2-a7298808771e ro quiet splash 
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing CPU#0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: using PIT calibration value
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected 2210.001 MHz processor.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Console: colour VGA+ 80x25
Jan 17 01:00:38 euskaltel kernel: [    0.004000] console [tty0] enabled
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Memory: 893820k/916352k available (2585k kernel code, 21936k reserved, 1164k data, 428k init, 0k highmem)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] virtual kernel memory layout:
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf7ee0000   ( 894 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .data : 0xc03864c8 - 0xc04a9680   (1164 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .text : 0xc0100000 - 0xc03864c8   (2585 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 17 01:00:38 euskaltel kernel: [    0.004000] hpet clockevent registered
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.00 BogoMIPS (lpj=8840004)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Security Framework initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SELinux:  Disabled at boot.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] AppArmor: AppArmor initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Mount-cache hash table entries: 512
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys ns
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys cpuacct
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys memory
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] using C1E aware idle routine
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking 'hlt' instruction... OK.
Jan 17 01:00:38 euskaltel kernel: [    0.016301] SMP alternatives: switching to UP code
Jan 17 01:00:38 euskaltel kernel: [    0.020009] ACPI: Core revision 20080609
Jan 17 01:00:38 euskaltel kernel: [    0.022070] ACPI: Checking initramfs for custom DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.328299] ENABLING IO-APIC IRQs
Jan 17 01:00:38 euskaltel kernel: [    0.328524] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 17 01:00:38 euskaltel kernel: [    0.370956] CPU0: AMD Athlon(tm) Processor LE-1600 stepping 03
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Brought up 1 CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Total of 1 processors activated (4420.00 BogoMIPS).
Jan 17 01:00:38 euskaltel kernel: [    0.372023] CPU0 attaching NULL sched-domain.
Jan 17 01:00:38 euskaltel kernel: [    0.372023] net_namespace: 840 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Booting paravirtualized kernel on bare hardware
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Time:  0:00:17  Date: 01/17/10
Jan 17 01:00:38 euskaltel kernel: [    0.372023] NET: Registered protocol family 16
Jan 17 01:00:38 euskaltel kernel: [    0.372023] EISA bus registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: bus type pci registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG area at f0000000 reserved in E820
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using MMCONFIG for extended config space
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using configuration type 1 for base access
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: EC: Look up EC in DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.379182] ACPI: Interpreter enabled
Jan 17 01:00:38 euskaltel kernel: [    0.379185] ACPI: (supports S0 S3 S4 S5)
Jan 17 01:00:38 euskaltel kernel: [    0.379199] ACPI: Using IOAPIC for interrupt routing
Jan 17 01:00:38 euskaltel kernel: [    0.389348] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 17 01:00:38 euskaltel kernel: [    0.389538] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
Jan 17 01:00:38 euskaltel kernel: [    0.389570] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389580] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389584] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
Jan 17 01:00:38 euskaltel kernel: [    0.389607] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389612] pci 0000:00:01.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389652] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.389676] pci 0000:00:02.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389678] pci 0000:00:02.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389680] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389683] pci 0000:00:02.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389701] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
Jan 17 01:00:38 euskaltel kernel: [    0.389731] pci 0000:00:02.1: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389732] pci 0000:00:02.1: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389734] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389738] pci 0000:00:02.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389790] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
Jan 17 01:00:38 euskaltel kernel: [    0.389820] pci 0000:00:05.0: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389823] pci 0000:00:05.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389850] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
Jan 17 01:00:38 euskaltel kernel: [    0.389884] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389888] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
Jan 17 01:00:38 euskaltel kernel: [    0.389914] pci 0000:00:07.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389916] pci 0000:00:07.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389918] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389922] pci 0000:00:07.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389937] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
Jan 17 01:00:38 euskaltel kernel: [    0.389941] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
Jan 17 01:00:38 euskaltel kernel: [    0.389944] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
Jan 17 01:00:38 euskaltel kernel: [    0.389948] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
Jan 17 01:00:38 euskaltel kernel: [    0.389951] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
Jan 17 01:00:38 euskaltel kernel: [    0.389955] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389985] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
Jan 17 01:00:38 euskaltel kernel: [    0.389989] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
Jan 17 01:00:38 euskaltel kernel: [    0.389992] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
Jan 17 01:00:38 euskaltel kernel: [    0.389996] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
Jan 17 01:00:38 euskaltel kernel: [    0.389999] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
Jan 17 01:00:38 euskaltel kernel: [    0.390003] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390052] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390055] pci 0000:00:09.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390084] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390087] pci 0000:00:0b.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390115] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390118] pci 0000:00:0c.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390129] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390134] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390139] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390144] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390248] pci 0000:00:04.0: transparent bridge
Jan 17 01:00:38 euskaltel kernel: [    0.390251] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390254] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390257] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390290] PCI: bridge 0000:00:09.0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.390293] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390296] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390329] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390331] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390335] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390367] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390369] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390381] bus 00 -> node 0
Jan 17 01:00:38 euskaltel kernel: [    0.390389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.390753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.442082] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442278] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442472] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442666] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442860] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443054] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443248] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443442] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443639] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.443832] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444034] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444235] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Jan 17 01:00:38 euskaltel kernel: [    0.444430] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444624] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444820] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445019] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445214] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.445410] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445609] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445853] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446091] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446327] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446563] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446799] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447036] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447272] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447508] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447744] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.447984] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448231] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448468] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.448706] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448943] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449180] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449417] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449655] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449892] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450128] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450292] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 17 01:00:38 euskaltel kernel: [    0.450319] pnp: PnP ACPI init
Jan 17 01:00:38 euskaltel kernel: [    0.450325] ACPI: bus type pnp registered
Jan 17 01:00:38 euskaltel kernel: [    0.455979] pnp: PnP ACPI: found 12 devices
Jan 17 01:00:38 euskaltel kernel: [    0.455981] ACPI: ACPI bus type pnp unregistered
Jan 17 01:00:38 euskaltel kernel: [    0.455983] PnPBIOS: Disabled by ACPI PNP
Jan 17 01:00:38 euskaltel kernel: [    0.456252] PCI: Using ACPI for IRQ routing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 8
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 20
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel: Initializing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  domain hash size = 128
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  unlabeled traffic allowed by default
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: 3 32-bit timers, 25000000 Hz
Jan 17 01:00:38 euskaltel kernel: [    0.457996] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.457998]    actual entries 65620
Jan 17 01:00:38 euskaltel kernel: [    0.458152] AppArmor: AppArmor Filesystem Enabled
Jan 17 01:00:38 euskaltel kernel: [    0.458176] ACPI: RTC can wake from S4
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1000-0x107f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1400-0x147f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1800-0x187f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2000-0x207f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2080-0x20ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x295-0x314 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x38000000-0x3fffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.460042] Switched to high resolution mode on CPU 0
Jan 17 01:00:38 euskaltel kernel: [    0.493510] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Jan 17 01:00:38 euskaltel kernel: [    0.493513] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
Jan 17 01:00:38 euskaltel kernel: [    0.493516] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493520] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jan 17 01:00:38 euskaltel kernel: [    0.493524] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Jan 17 01:00:38 euskaltel kernel: [    0.493527] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Jan 17 01:00:38 euskaltel kernel: [    0.493530] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
Jan 17 01:00:38 euskaltel kernel: [    0.493533] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493536] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Jan 17 01:00:38 euskaltel kernel: [    0.493539] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Jan 17 01:00:38 euskaltel kernel: [    0.493542] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493545] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493548] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Jan 17 01:00:38 euskaltel kernel: [    0.493551] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Jan 17 01:00:38 euskaltel kernel: [    0.493554] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Jan 17 01:00:38 euskaltel kernel: [    0.493557] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493565] pci 0000:00:04.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493570] pci 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493575] pci 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493579] pci 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493582] bus: 00 index 0 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493584] bus: 00 index 1 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493586] bus: 01 index 0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.493588] bus: 01 index 1 mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493590] bus: 01 index 2 mmio: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493592] bus: 01 index 3 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493594] bus: 01 index 4 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493596] bus: 02 index 0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.493598] bus: 02 index 1 mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493600] bus: 02 index 2 mmio: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493602] bus: 02 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493604] bus: 03 index 0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493606] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493608] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493610] bus: 03 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493612] bus: 04 index 0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493614] bus: 04 index 1 mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493616] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493617] bus: 04 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493627] NET: Registered protocol family 2
Jan 17 01:00:38 euskaltel kernel: [    0.493763] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494036] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494820] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.495192] TCP: Hash tables configured (established 131072 bind 65536)
Jan 17 01:00:38 euskaltel kernel: [    0.495194] TCP reno registered
Jan 17 01:00:38 euskaltel kernel: [    0.495327] NET: Registered protocol family 1
Jan 17 01:00:38 euskaltel kernel: [    0.495434] checking if image is initramfs... it is
Jan 17 01:00:38 euskaltel kernel: [    1.115818] Freeing initrd memory: 7960k freed
Jan 17 01:00:38 euskaltel kernel: [    1.116448] audit: initializing netlink socket (disabled)
Jan 17 01:00:38 euskaltel kernel: [    1.116461] type=2000 audit(1263686417.116:1): initialized
Jan 17 01:00:38 euskaltel kernel: [    1.121466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 17 01:00:38 euskaltel kernel: [    1.123323] VFS: Disk quotas dquot_6.5.1
Jan 17 01:00:38 euskaltel kernel: [    1.123393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 17 01:00:38 euskaltel kernel: [    1.123487] msgmni has been set to 1761
Jan 17 01:00:38 euskaltel kernel: [    1.123588] io scheduler noop registered
Jan 17 01:00:38 euskaltel kernel: [    1.123590] io scheduler anticipatory registered
Jan 17 01:00:38 euskaltel kernel: [    1.123592] io scheduler deadline registered
Jan 17 01:00:38 euskaltel kernel: [    1.123602] io scheduler cfq registered (default)
Jan 17 01:00:38 euskaltel kernel: [    1.123635] pci 0000:00:00.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136045] pci 0000:00:04.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136061] pci 0000:00:05.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136087] pci 0000:00:07.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136101] pci 0000:00:08.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136115] pci 0000:00:08.1: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136130] pci 0000:00:09.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136144] pci 0000:00:0b.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136159] pci 0000:00:0c.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136173] pci 0000:00:0d.0: Boot video device
Jan 17 01:00:38 euskaltel kernel: [    1.136260] pcieport-driver 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136282] pcieport-driver 0000:00:09.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136300] pci_express 0000:00:09.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136332] pci_express 0000:00:09.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136386] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136407] pcieport-driver 0000:00:0b.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136422] pci_express 0000:00:0b.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136451] pci_express 0000:00:0b.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136504] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136524] pcieport-driver 0000:00:0c.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136539] pci_express 0000:00:0c.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136569] pci_express 0000:00:0c.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136783] isapnp: Scanning for PnP cards...
Jan 17 01:00:38 euskaltel kernel: [    1.489432] isapnp: No Plug & Play device found
Jan 17 01:00:38 euskaltel kernel: [    1.519451] hpet_resources: 0xfeff0000 is busy
Jan 17 01:00:38 euskaltel kernel: [    1.519522] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 17 01:00:38 euskaltel kernel: [    1.521642] brd: module loaded
Jan 17 01:00:38 euskaltel kernel: [    1.521708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 17 01:00:38 euskaltel kernel: [    1.521800] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 17 01:00:38 euskaltel kernel: [    1.522162] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 17 01:00:38 euskaltel kernel: [    1.522166] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 17 01:00:38 euskaltel kernel: [    1.522464] mice: PS/2 mouse device common for all mice
Jan 17 01:00:38 euskaltel kernel: [    1.522576] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jan 17 01:00:38 euskaltel kernel: [    1.522610] rtc0: alarms up to one year, y3k, hpet irqs
Jan 17 01:00:38 euskaltel kernel: [    1.522699] EISA: Probing bus 0 at eisa.0
Jan 17 01:00:38 euskaltel kernel: [    1.522704] Cannot allocate resource for EISA slot 1
Jan 17 01:00:38 euskaltel kernel: [    1.522707] Cannot allocate resource for EISA slot 2
Jan 17 01:00:38 euskaltel kernel: [    1.522720] Cannot allocate resource for EISA slot 8
Jan 17 01:00:38 euskaltel kernel: [    1.522722] EISA: Detected 0 cards.
Jan 17 01:00:38 euskaltel kernel: [    1.522725] cpuidle: using governor ladder
Jan 17 01:00:38 euskaltel kernel: [    1.522727] cpuidle: using governor menu
Jan 17 01:00:38 euskaltel kernel: [    1.523155] TCP cubic registered
Jan 17 01:00:38 euskaltel kernel: [    1.523179] Using IPI No-Shortcut mode
Jan 17 01:00:38 euskaltel kernel: [    1.523328] registered taskstats version 1
Jan 17 01:00:38 euskaltel kernel: [    1.523443]   Magic number: 10:203:1
Jan 17 01:00:38 euskaltel kernel: [    1.523450] tty ttye9: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523461] tty ttybc: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523652] rtc_cmos 00:05: setting system clock to 2010-01-17 00:00:18 UTC (1263686418)
Jan 17 01:00:38 euskaltel kernel: [    1.523655] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 17 01:00:38 euskaltel kernel: [    1.523657] EDD information not available.
Jan 17 01:00:38 euskaltel kernel: [    1.524041] Freeing unused kernel memory: 428k freed
Jan 17 01:00:38 euskaltel kernel: [    1.524109] Write protecting the kernel text: 2588k
Jan 17 01:00:38 euskaltel kernel: [    1.524147] Write protecting the kernel read-only data: 940k
Jan 17 01:00:38 euskaltel kernel: [    1.544813] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 17 01:00:38 euskaltel kernel: [    1.744060] fuse init (API version 7.9)
Jan 17 01:00:38 euskaltel kernel: [    1.862062] fan PNP0C0B:00: registered as cooling_device0
Jan 17 01:00:38 euskaltel kernel: [    1.862067] ACPI: Fan [FAN] (on)
Jan 17 01:00:38 euskaltel kernel: [    1.868784] processor ACPI0007:00: registered as cooling_device1
Jan 17 01:00:38 euskaltel kernel: [    1.870876] ACPI: Expecting a [Reference] package element, found type 0
Jan 17 01:00:38 euskaltel kernel: [    1.871083] thermal LNXTHERM:01: registered as thermal_zone0
Jan 17 01:00:38 euskaltel kernel: [    1.871449] ACPI: Thermal Zone [THRM] (30 C)
Jan 17 01:00:38 euskaltel kernel: [    2.744077] usbcore: registered new interface driver usbfs
Jan 17 01:00:38 euskaltel kernel: [    2.744101] usbcore: registered new interface driver hub
Jan 17 01:00:38 euskaltel kernel: [    2.752175] No dock devices found.
Jan 17 01:00:38 euskaltel kernel: [    2.784050] usbcore: registered new device driver usb
Jan 17 01:00:38 euskaltel kernel: [    2.809697] SCSI subsystem initialized
Jan 17 01:00:38 euskaltel kernel: [    2.809760] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jan 17 01:00:38 euskaltel kernel: [    2.810181] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810191] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810196] forcedeth 0000:00:07.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    2.814686] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 17 01:00:38 euskaltel kernel: [    2.831542] libata version 3.00 loaded.
Jan 17 01:00:38 euskaltel kernel: [    3.328497] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:72:a9:fe:35
Jan 17 01:00:38 euskaltel kernel: [    3.328502] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Jan 17 01:00:38 euskaltel kernel: [    3.328958] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328970] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328984] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.328987] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.329023] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Jan 17 01:00:38 euskaltel kernel: [    3.329045] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Jan 17 01:00:38 euskaltel kernel: [    3.386211] usb usb1: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.386319] hub 1-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.386328] hub 1-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.592901] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592911] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 20 (level, low) -> IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592921] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592923] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.592944] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Jan 17 01:00:38 euskaltel kernel: [    3.592966] ehci_hcd 0000:00:02.1: debug port 1
Jan 17 01:00:38 euskaltel kernel: [    3.592970] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 17 01:00:38 euskaltel kernel: [    3.592984] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
Jan 17 01:00:38 euskaltel kernel: [    3.604016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 17 01:00:38 euskaltel kernel: [    3.604090] usb usb2: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.604113] hub 2-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.604120] hub 2-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.817083] sata_nv 0000:00:08.0: version 3.5
Jan 17 01:00:38 euskaltel kernel: [    3.817493] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817503] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817543] sata_nv 0000:00:08.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.820082] scsi0 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821181] scsi1 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821357] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Jan 17 01:00:38 euskaltel kernel: [    3.821360] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.076014] usb 2-8: new high speed USB device using ehci_hcd and address 3
Jan 17 01:00:38 euskaltel kernel: [    4.608032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    4.616299] ata2.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.616302] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 17 01:00:38 euskaltel kernel: [    4.632527] ata2.00: configured for UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.632609] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    4.633103] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633108] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633148] sata_nv 0000:00:08.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    4.633465] scsi2 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633673] scsi3 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633831] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.633834] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.763877] usb 2-8: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    5.072017] usb 1-2: new full speed USB device using ohci_hcd and address 2
Jan 17 01:00:38 euskaltel kernel: [    5.100033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    5.108119] ata3.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.124122] ata3.00: configured for UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.293649] usb 1-2: configuration #1 chosen from 2 choices
Jan 17 01:00:38 euskaltel kernel: [    5.312194] usbcore: registered new interface driver libusual
Jan 17 01:00:38 euskaltel kernel: [    5.324111] Initializing USB Mass Storage driver...
Jan 17 01:00:38 euskaltel kernel: [    5.325593] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 17 01:00:38 euskaltel kernel: [    5.325675] usbcore: registered new interface driver usb-storage
Jan 17 01:00:38 euskaltel kernel: [    5.325678] USB Mass Storage support registered.
Jan 17 01:00:38 euskaltel kernel: [    5.325753] usb-storage: device found at 3
Jan 17 01:00:38 euskaltel kernel: [    5.325754] usb-storage: waiting for device to settle before scanning
Jan 17 01:00:38 euskaltel kernel: [    5.334886] scsi 1:0:0:0: Attached scsi generic sg0 type 0
Jan 17 01:00:38 euskaltel kernel: [    5.449650] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    5.449776] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Jan 17 01:00:38 euskaltel kernel: [    5.449816] pata_amd 0000:00:06.0: version 0.3.10
Jan 17 01:00:38 euskaltel kernel: [    5.449860] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.450312] scsi5 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.450553] scsi6 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.451328] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 17 01:00:38 euskaltel kernel: [    5.451332] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 17 01:00:38 euskaltel kernel: [    5.614957] ata6: port disabled. ignoring.
Jan 17 01:00:38 euskaltel kernel: [    5.656068] Driver 'sd' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.656157] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656171] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656173] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656192] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656251] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656261] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656264] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656282] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656285]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.679675]  sda1 sda2 < sda5 >
Jan 17 01:00:38 euskaltel kernel: [    5.705190] sd 1:0:0:0: [sda] Attached SCSI disk
Jan 17 01:00:38 euskaltel kernel: [    5.717880] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 17 01:00:38 euskaltel kernel: [    5.717885] Uniform CD-ROM driver Revision: 3.20
Jan 17 01:00:38 euskaltel kernel: [    5.717972] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 17 01:00:38 euskaltel kernel: [    5.869216] PM: Starting manual resume from disk
Jan 17 01:00:38 euskaltel kernel: [    5.869219] PM: Resume from partition 8:5
Jan 17 01:00:38 euskaltel kernel: [    5.869221] PM: Checking hibernation image.
Jan 17 01:00:38 euskaltel kernel: [    5.869321] PM: Resume from disk failed.
Jan 17 01:00:38 euskaltel kernel: [    5.923899] kjournald starting.  Commit interval 5 seconds
Jan 17 01:00:38 euskaltel kernel: [    5.923910] EXT3-fs: mounted filesystem with ordered data mode.
Jan 17 01:00:38 euskaltel kernel: [   10.324166] usb-storage: device scan complete
Jan 17 01:00:38 euskaltel kernel: [   10.330532] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Jan 17 01:00:38 euskaltel kernel: [   10.331710] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 17 01:00:38 euskaltel kernel: [   10.331831] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 17 01:00:38 euskaltel kernel: [   12.116177] udevd version 124 started
Jan 17 01:00:38 euskaltel kernel: [   12.580180] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Jan 17 01:00:38 euskaltel kernel: [   12.580209] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
Jan 17 01:00:38 euskaltel kernel: [   13.024208] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 17 01:00:38 euskaltel kernel: [   13.040031] ACPI: Power Button (FF) [PWRF]
Jan 17 01:00:38 euskaltel kernel: [   13.040103] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Jan 17 01:00:38 euskaltel kernel: [   13.056033] ACPI: Power Button (CM) [PWRB]
Jan 17 01:00:38 euskaltel kernel: [   13.064162] ACPI: WMI: Mapper loaded
Jan 17 01:00:38 euskaltel kernel: [   13.984598] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984604] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984631] HDA Intel 0000:00:05.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   15.208291] eth1: register 'cdc_ether' at usb-0000:00:02.0-2, CDC Ethernet Device, 00:18:68:0a:59:75
Jan 17 01:00:38 euskaltel kernel: [   15.208311] usbcore: registered new interface driver cdc_ether
Jan 17 01:00:38 euskaltel kernel: [   15.366813] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 17 01:00:38 euskaltel kernel: [   15.393091] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 17 01:00:38 euskaltel kernel: [   15.457623] Linux agpgart interface v0.103
Jan 17 01:00:38 euskaltel kernel: [   15.638236] nvidia: module license 'NVIDIA' taints kernel.
Jan 17 01:00:38 euskaltel kernel: [   16.015092] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015098] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015105] nvidia 0000:00:0d.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   16.015355] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
Jan 17 01:00:38 euskaltel kernel: [   16.140880] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jan 17 01:00:38 euskaltel kernel: [   16.823744] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jan 17 01:00:38 euskaltel kernel: [   17.178460] udev: renamed network interface eth1 to eth2
Jan 17 01:00:38 euskaltel kernel: [   18.116894] lp: driver loaded but no devices found
Jan 17 01:00:38 euskaltel kernel: [   18.320383] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
Jan 17 01:00:38 euskaltel kernel: [   18.870393] EXT3 FS on sda1, internal journal
Jan 17 01:00:38 euskaltel kernel: [   20.073620] type=1505 audit(1263686437.081:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4096
Jan 17 01:00:38 euskaltel kernel: [   20.259552] type=1505 audit(1263686437.265:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.259778] type=1505 audit(1263686437.265:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.415348] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 17 01:00:38 euskaltel kernel: [   21.109118] powernow-k8: Found 1 AMD Athlon(tm) Processor LE-1600 processors (1 cpu cores) (version 2.20.00)
Jan 17 01:00:38 euskaltel kernel: [   21.109155] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
Jan 17 01:00:38 euskaltel kernel: [   21.109157] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
Jan 17 01:00:38 euskaltel kernel: [   21.109159] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
Jan 17 01:00:38 euskaltel kernel: [   21.109161] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jan 17 01:00:38 euskaltel kernel: [   21.923180] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped root privileges.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: avahi-daemon 0.6.23 starting up.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully called chroot().
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped remaining capabilities.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: No service file found in /etc/avahi/services.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Network interface enumeration completed.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Server startup complete. Host name is euskaltel.local. Local service cookie is 3919910173.
Jan 17 01:00:40 euskaltel avguard.bin[4798]: Info: Using library for dazuko version 3 
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: failed to register with Dazuko
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: termination of process 4807 (Guard scanner): connecting dazuko failed
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: On-Access protection is lost.
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: No dazuko module available, on-access protection disabled.
Jan 17 01:00:46 euskaltel kernel: [   29.634910] ppdev: user-space parallel port driver
Jan 17 01:00:49 euskaltel dhcdbd: Started up.
Jan 17 01:00:50 euskaltel acpid: client connected from 5167[111:123] 
Jan 17 01:00:50 euskaltel kernel: [   33.633134] eth0: no link during initialization.
Jan 17 01:00:51 euskaltel kernel: [   34.500016] Clocksource tsc unstable (delta = -90874311 ns)
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 104 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 135 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_keys: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:52 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:52 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
Jan 17 01:00:53 euskaltel /usr/sbin/cron[5347]: (CRON) INFO (pidfile fd = 3)
Jan 17 01:00:53 euskaltel /usr/sbin/cron[5348]: (CRON) STARTUP (fork ok)
Jan 17 01:00:53 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:53 euskaltel /usr/sbin/cron[5348]: (CRON) INFO (Running @reboot jobs)
Jan 17 01:00:55 euskaltel kernel: [   38.516037] NET: Registered protocol family 17
Jan 17 01:00:58 euskaltel dhclient: DHCPREQUEST of 85.84.234.186 on eth2 to 255.255.255.255 port 67
Jan 17 01:00:58 euskaltel dhclient: DHCPACK of 85.84.234.186 from 10.77.128.1
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel dhclient: bound to 85.84.234.186 -- renewal in 35752 seconds.
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.host_name
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_domain
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_servers
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.interface_mtu
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:59 euskaltel kernel: [   42.926947] NET: Registered protocol family 10
Jan 17 01:00:59 euskaltel kernel: [   42.928576] lo: Disabled Privacy Extensions
Jan 17 01:00:59 euskaltel kernel: [   42.929484] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 17 01:01:00 euskaltel ntpdate[5551]: adjust time server 91.189.94.4 offset -0.147056 sec
Jan 17 01:01:01 euskaltel avahi-daemon[4720]: Registering new address record for fe80::218:68ff:fe0a:5975 on eth2.*.
Jan 17 01:01:10 euskaltel kernel: [   53.888014] eth2: no IPv6 routers present
Jan 17 01:10:02 euskaltel /USR/SBIN/CRON[5569]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:17:01 euskaltel /USR/SBIN/CRON[5651]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 17 01:20:01 euskaltel /USR/SBIN/CRON[5695]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:30:01 euskaltel /USR/SBIN/CRON[5778]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:40:01 euskaltel /USR/SBIN/CRON[5861]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:50:01 euskaltel /USR/SBIN/CRON[5944]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 02:00:01 euskaltel /USR/SBIN/CRON[6027]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 02:10:01 euskaltel /USR/SBIN/CRON[6110]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 02:17:01 euskaltel /USR/SBIN/CRON[6193]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 17 02:18:28 euskaltel init: tty4 main process (4296) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty5 main process (4297) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty2 main process (4304) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty3 main process (4305) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty6 main process (4306) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty1 main process (5457) killed by TERM signal
Jan 17 02:18:29 euskaltel acpid: client 5259[0:0] has disconnected 
Jan 17 02:18:29 euskaltel acpid: client 5259[0:0] has disconnected 
Jan 17 02:18:29 euskaltel avguard.bin[4805]: Info: service terminated. Shutting down
Jan 17 02:18:36 euskaltel avahi-daemon[4720]: Got SIGTERM, quitting.
Jan 17 02:18:36 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 02:18:36 euskaltel exiting on signal 15
```

Why does this annoying anomaly happen? Virus (unlikely because I made a whole system scan less than a week ago)? Just the usual crazy Ubuntu bug, which was maybe even intended as feature? Has my PC (AMD Athlon 64) acquired life of its own?

The PC (cheapest in market here) has not a power switch, tough I guess I can always pull out the power plug but really I'd like it to sleep all the way until I click on the on/off button, as it used to.

Thanks in advance

---

### Post by stinkeye on 2010-01-16
Check your bios settings.

---

### Post by dnvikram on 2010-01-16
> **Maju said:**
> Hello, I recently had the (dubiously good) idea of upgrading my Hardy Heron to Intrepid Ibex (actually I hoped to get directly into a more advanced version but guess not). Since then I have a very strange issue (I have searched and found nothing alike except [this thread]("http://ubuntuforums.org/showthread.php?t=765401&highlight=starts+alone")):

At 1:00 the computer starts on its own, with the side effects of wasting electricity and waking me up. After taking off schedulers and other stuff that looked like unnecessary (based on searchs in this forum), it still does it, producing the following logs:

```
Jan 17 01:00:39 euskaltel sudo:     root : unable to resolve host euskaltel
Jan 17 01:00:39 euskaltel sudo:     root : TTY=console ; PWD=/ ; USER=root ; COMMAND=/sbin/insmod -f /lib/modules/2.6.27-16-generic/kernel/drivers/char/agrmodem.ko
Jan 17 01:00:39 euskaltel sudo:     root : unable to resolve host euskaltel
Jan 17 01:00:39 euskaltel sudo:     root : TTY=console ; PWD=/ ; USER=root ; COMMAND=/sbin/insmod -f /lib/modules/2.6.27-16-generic/kernel/drivers/char/agrserial.ko
Jan 17 01:10:01 euskaltel CRON[5561]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:10:05 euskaltel CRON[5561]: pam_unix(cron:session): session closed for user root
Jan 17 01:17:01 euskaltel CRON[5645]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:17:01 euskaltel CRON[5645]: pam_unix(cron:session): session closed for user root
Jan 17 01:20:01 euskaltel CRON[5689]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:20:02 euskaltel CRON[5689]: pam_unix(cron:session): session closed for user root
Jan 17 01:30:01 euskaltel CRON[5772]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:30:02 euskaltel CRON[5772]: pam_unix(cron:session): session closed for user root
Jan 17 01:40:01 euskaltel CRON[5855]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:40:01 euskaltel CRON[5855]: pam_unix(cron:session): session closed for user root
Jan 17 01:50:01 euskaltel CRON[5938]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 01:50:01 euskaltel CRON[5938]: pam_unix(cron:session): session closed for user root
Jan 17 02:00:01 euskaltel CRON[6021]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 02:00:02 euskaltel CRON[6021]: pam_unix(cron:session): session closed for user root
Jan 17 02:10:01 euskaltel CRON[6104]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 02:10:02 euskaltel CRON[6104]: pam_unix(cron:session): session closed for user root
Jan 17 02:17:01 euskaltel CRON[6187]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 17 02:17:01 euskaltel CRON[6187]: pam_unix(cron:session): session closed for user root
```

```
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped root privileges.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: avahi-daemon 0.6.23 starting up.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully called chroot().
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped remaining capabilities.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: No service file found in /etc/avahi/services.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Network interface enumeration completed.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Server startup complete. Host name is euskaltel.local. Local service cookie is 3919910173.
Jan 17 01:00:50 euskaltel acpid: client connected from 5167[111:123] 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 104 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 135 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_keys: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:52 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:53 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:58 euskaltel dhclient: DHCPREQUEST of 85.84.234.186 on eth2 to 255.255.255.255 port 67
Jan 17 01:00:58 euskaltel dhclient: DHCPACK of 85.84.234.186 from 10.77.128.1
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel dhclient: bound to 85.84.234.186 -- renewal in 35752 seconds.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:01:00 euskaltel ntpdate[5551]: adjust time server 91.189.94.4 offset -0.147056 sec
Jan 17 01:01:01 euskaltel avahi-daemon[4720]: Registering new address record for fe80::218:68ff:fe0a:5975 on eth2.*.
Jan 17 02:18:28 euskaltel init: tty4 main process (4296) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty5 main process (4297) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty2 main process (4304) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty3 main process (4305) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty6 main process (4306) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty1 main process (5457) killed by TERM signal
```

This last is obviously my manually turning it off. 

```
Jan 17 01:00:38 euskaltel kernel: [    0.000000] kernel direct mapping tables up to 37ee0000 @ 10000-16000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] On node 0 totalpages: 228975
Jan 17 01:00:38 euskaltel kernel: [    0.000000] free_area_init_node: node 0, pgdat c048e700, node_mem_map c1000240
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal zone: 223014 pages, LIFO batch:31
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jan 17 01:00:38 euskaltel kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jan 17 01:00:38 euskaltel kernel: [    0.004000] hpet clockevent registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] CPU0 attaching NULL sched-domain.
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: EC: Look up EC in DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.389538] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
Jan 17 01:00:38 euskaltel kernel: [    0.389570] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389580] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389584] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
Jan 17 01:00:38 euskaltel kernel: [    0.389652] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.389676] pci 0000:00:02.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389678] pci 0000:00:02.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389701] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
Jan 17 01:00:38 euskaltel kernel: [    0.389731] pci 0000:00:02.1: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389732] pci 0000:00:02.1: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389790] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
Jan 17 01:00:38 euskaltel kernel: [    0.389850] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
Jan 17 01:00:38 euskaltel kernel: [    0.389884] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389888] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
Jan 17 01:00:38 euskaltel kernel: [    0.389914] pci 0000:00:07.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389916] pci 0000:00:07.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389937] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
Jan 17 01:00:38 euskaltel kernel: [    0.389941] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
Jan 17 01:00:38 euskaltel kernel: [    0.389944] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
Jan 17 01:00:38 euskaltel kernel: [    0.389948] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
Jan 17 01:00:38 euskaltel kernel: [    0.389951] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
Jan 17 01:00:38 euskaltel kernel: [    0.389955] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389985] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
Jan 17 01:00:38 euskaltel kernel: [    0.389989] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
Jan 17 01:00:38 euskaltel kernel: [    0.389992] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
Jan 17 01:00:38 euskaltel kernel: [    0.389996] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
Jan 17 01:00:38 euskaltel kernel: [    0.389999] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
Jan 17 01:00:38 euskaltel kernel: [    0.390003] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390129] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390134] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390139] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390144] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390251] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390254] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390257] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390290] PCI: bridge 0000:00:09.0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.390293] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390296] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390329] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390331] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390335] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390367] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390369] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390381] bus 00 -> node 0
Jan 17 01:00:38 euskaltel kernel: [    0.390389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.390753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.460042] Switched to high resolution mode on CPU 0
Jan 17 01:00:38 euskaltel kernel: [    0.493565] pci 0000:00:04.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493570] pci 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493575] pci 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493579] pci 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136173] pci 0000:00:0d.0: Boot video device
Jan 17 01:00:38 euskaltel kernel: [    1.136260] pcieport-driver 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136300] pci_express 0000:00:09.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136332] pci_express 0000:00:09.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136386] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136422] pci_express 0000:00:0b.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136451] pci_express 0000:00:0b.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136504] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136539] pci_express 0000:00:0c.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136569] pci_express 0000:00:0c.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.519451] hpet_resources: 0xfeff0000 is busy
Jan 17 01:00:38 euskaltel kernel: [    2.810196] forcedeth 0000:00:07.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    2.814686] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 17 01:00:38 euskaltel kernel: [    2.831542] libata version 3.00 loaded.
Jan 17 01:00:38 euskaltel kernel: [    3.328984] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592921] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592970] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 17 01:00:38 euskaltel kernel: [    3.817083] sata_nv 0000:00:08.0: version 3.5
Jan 17 01:00:38 euskaltel kernel: [    3.817543] sata_nv 0000:00:08.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    4.633148] sata_nv 0000:00:08.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.325753] usb-storage: device found at 3
Jan 17 01:00:38 euskaltel kernel: [    5.325754] usb-storage: waiting for device to settle before scanning
Jan 17 01:00:38 euskaltel kernel: [    5.449816] pata_amd 0000:00:06.0: version 0.3.10
Jan 17 01:00:38 euskaltel kernel: [    5.449860] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.614957] ata6: port disabled. ignoring.
Jan 17 01:00:38 euskaltel kernel: [    5.656173] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656264] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.717972] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 17 01:00:38 euskaltel kernel: [    5.869219] PM: Resume from partition 8:5
Jan 17 01:00:38 euskaltel kernel: [    5.869221] PM: Checking hibernation image.
Jan 17 01:00:38 euskaltel kernel: [    5.869321] PM: Resume from disk failed.
Jan 17 01:00:38 euskaltel kernel: [   10.324166] usb-storage: device scan complete
Jan 17 01:00:38 euskaltel kernel: [   13.984631] HDA Intel 0000:00:05.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   16.015105] nvidia 0000:00:0d.0: setting latency timer to 64
Jan 17 01:01:10 euskaltel kernel: [   53.888014] eth2: no IPv6 routers present
```

```
Jan 17 01:00:38 euskaltel kernel: Inspecting /boot/System.map-2.6.27-16-generic
Jan 17 01:00:38 euskaltel kernel: Cannot find map file.
Jan 17 01:00:38 euskaltel kernel: Loaded 67477 symbols from 83 modules.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Linux version 2.6.27-16-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Dec 1 17:56:54 UTC 2009 (Ubuntu 2.6.27-16.44-generic)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] DMI 2.5 present.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] kernel direct mapping tables up to 37ee0000 @ 10000-16000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] RAMDISK: 37709000 - 37ecf0f3
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDT 37EE3000, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACP 37EE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: DSDT 37EE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACS 37EE0000, 0040
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: SSDT 37EEA000, 0115 (r1 PTLTD  POWERNOW        1  LTP        1)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET 37EEA140, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA       98)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: MCFG 37EEA180, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: APIC 37EE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 0MB HIGHMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 894MB LOWMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   mapped low ram: 0 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   low ram: 00000000 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   bootmap 00012000 - 00018fdc
Jan 17 01:00:38 euskaltel kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ee0000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #4 [0037709000 - 0037ecf0f3]          RAMDISK ==> [0037709000 - 0037ecf0f3]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Zone PFN ranges:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal   0x00001000 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   HighMem  0x00037ee0 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Movable zone start PFN for each node
Jan 17 01:00:38 euskaltel kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000100 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] On node 0 totalpages: 228975
Jan 17 01:00:38 euskaltel kernel: [    0.000000] free_area_init_node: node 0, pgdat c048e700, node_mem_map c1000240
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal zone: 223014 pages, LIFO batch:31
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 17 01:00:38 euskaltel kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jan 17 01:00:38 euskaltel kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226961
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Kernel command line: root=UUID=f825bb92-55a9-4133-bbf2-a7298808771e ro quiet splash 
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing CPU#0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: using PIT calibration value
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected 2210.001 MHz processor.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Console: colour VGA+ 80x25
Jan 17 01:00:38 euskaltel kernel: [    0.004000] console [tty0] enabled
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Memory: 893820k/916352k available (2585k kernel code, 21936k reserved, 1164k data, 428k init, 0k highmem)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] virtual kernel memory layout:
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf7ee0000   ( 894 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .data : 0xc03864c8 - 0xc04a9680   (1164 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .text : 0xc0100000 - 0xc03864c8   (2585 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 17 01:00:38 euskaltel kernel: [    0.004000] hpet clockevent registered
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.00 BogoMIPS (lpj=8840004)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Security Framework initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SELinux:  Disabled at boot.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] AppArmor: AppArmor initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Mount-cache hash table entries: 512
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys ns
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys cpuacct
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys memory
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] using C1E aware idle routine
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking 'hlt' instruction... OK.
Jan 17 01:00:38 euskaltel kernel: [    0.016301] SMP alternatives: switching to UP code
Jan 17 01:00:38 euskaltel kernel: [    0.020009] ACPI: Core revision 20080609
Jan 17 01:00:38 euskaltel kernel: [    0.022070] ACPI: Checking initramfs for custom DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.328299] ENABLING IO-APIC IRQs
Jan 17 01:00:38 euskaltel kernel: [    0.328524] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 17 01:00:38 euskaltel kernel: [    0.370956] CPU0: AMD Athlon(tm) Processor LE-1600 stepping 03
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Brought up 1 CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Total of 1 processors activated (4420.00 BogoMIPS).
Jan 17 01:00:38 euskaltel kernel: [    0.372023] CPU0 attaching NULL sched-domain.
Jan 17 01:00:38 euskaltel kernel: [    0.372023] net_namespace: 840 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Booting paravirtualized kernel on bare hardware
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Time:  0:00:17  Date: 01/17/10
Jan 17 01:00:38 euskaltel kernel: [    0.372023] NET: Registered protocol family 16
Jan 17 01:00:38 euskaltel kernel: [    0.372023] EISA bus registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: bus type pci registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG area at f0000000 reserved in E820
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using MMCONFIG for extended config space
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using configuration type 1 for base access
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: EC: Look up EC in DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.379182] ACPI: Interpreter enabled
Jan 17 01:00:38 euskaltel kernel: [    0.379185] ACPI: (supports S0 S3 S4 S5)
Jan 17 01:00:38 euskaltel kernel: [    0.379199] ACPI: Using IOAPIC for interrupt routing
Jan 17 01:00:38 euskaltel kernel: [    0.389348] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 17 01:00:38 euskaltel kernel: [    0.389538] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
Jan 17 01:00:38 euskaltel kernel: [    0.389570] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389580] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389584] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
Jan 17 01:00:38 euskaltel kernel: [    0.389607] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389612] pci 0000:00:01.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389652] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.389676] pci 0000:00:02.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389678] pci 0000:00:02.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389680] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389683] pci 0000:00:02.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389701] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
Jan 17 01:00:38 euskaltel kernel: [    0.389731] pci 0000:00:02.1: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389732] pci 0000:00:02.1: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389734] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389738] pci 0000:00:02.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389790] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
Jan 17 01:00:38 euskaltel kernel: [    0.389820] pci 0000:00:05.0: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389823] pci 0000:00:05.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389850] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
Jan 17 01:00:38 euskaltel kernel: [    0.389884] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389888] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
Jan 17 01:00:38 euskaltel kernel: [    0.389914] pci 0000:00:07.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389916] pci 0000:00:07.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389918] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389922] pci 0000:00:07.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389937] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
Jan 17 01:00:38 euskaltel kernel: [    0.389941] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
Jan 17 01:00:38 euskaltel kernel: [    0.389944] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
Jan 17 01:00:38 euskaltel kernel: [    0.389948] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
Jan 17 01:00:38 euskaltel kernel: [    0.389951] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
Jan 17 01:00:38 euskaltel kernel: [    0.389955] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389985] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
Jan 17 01:00:38 euskaltel kernel: [    0.389989] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
Jan 17 01:00:38 euskaltel kernel: [    0.389992] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
Jan 17 01:00:38 euskaltel kernel: [    0.389996] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
Jan 17 01:00:38 euskaltel kernel: [    0.389999] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
Jan 17 01:00:38 euskaltel kernel: [    0.390003] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390052] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390055] pci 0000:00:09.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390084] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390087] pci 0000:00:0b.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390115] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390118] pci 0000:00:0c.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390129] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390134] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390139] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390144] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390248] pci 0000:00:04.0: transparent bridge
Jan 17 01:00:38 euskaltel kernel: [    0.390251] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390254] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390257] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390290] PCI: bridge 0000:00:09.0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.390293] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390296] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390329] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390331] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390335] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390367] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390369] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390381] bus 00 -> node 0
Jan 17 01:00:38 euskaltel kernel: [    0.390389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.390753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.442082] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442278] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442472] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442666] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442860] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443054] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443248] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443442] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443639] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.443832] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444034] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444235] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Jan 17 01:00:38 euskaltel kernel: [    0.444430] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444624] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444820] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445019] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445214] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.445410] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445609] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445853] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446091] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446327] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446563] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446799] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447036] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447272] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447508] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447744] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.447984] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448231] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448468] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.448706] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448943] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449180] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449417] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449655] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449892] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450128] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450292] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 17 01:00:38 euskaltel kernel: [    0.450319] pnp: PnP ACPI init
Jan 17 01:00:38 euskaltel kernel: [    0.450325] ACPI: bus type pnp registered
Jan 17 01:00:38 euskaltel kernel: [    0.455979] pnp: PnP ACPI: found 12 devices
Jan 17 01:00:38 euskaltel kernel: [    0.455981] ACPI: ACPI bus type pnp unregistered
Jan 17 01:00:38 euskaltel kernel: [    0.455983] PnPBIOS: Disabled by ACPI PNP
Jan 17 01:00:38 euskaltel kernel: [    0.456252] PCI: Using ACPI for IRQ routing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 8
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 20
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel: Initializing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  domain hash size = 128
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  unlabeled traffic allowed by default
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: 3 32-bit timers, 25000000 Hz
Jan 17 01:00:38 euskaltel kernel: [    0.457996] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.457998]    actual entries 65620
Jan 17 01:00:38 euskaltel kernel: [    0.458152] AppArmor: AppArmor Filesystem Enabled
Jan 17 01:00:38 euskaltel kernel: [    0.458176] ACPI: RTC can wake from S4
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1000-0x107f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1400-0x147f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1800-0x187f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2000-0x207f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2080-0x20ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x295-0x314 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x38000000-0x3fffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.460042] Switched to high resolution mode on CPU 0
Jan 17 01:00:38 euskaltel kernel: [    0.493510] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Jan 17 01:00:38 euskaltel kernel: [    0.493513] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
Jan 17 01:00:38 euskaltel kernel: [    0.493516] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493520] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jan 17 01:00:38 euskaltel kernel: [    0.493524] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Jan 17 01:00:38 euskaltel kernel: [    0.493527] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Jan 17 01:00:38 euskaltel kernel: [    0.493530] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
Jan 17 01:00:38 euskaltel kernel: [    0.493533] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493536] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Jan 17 01:00:38 euskaltel kernel: [    0.493539] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Jan 17 01:00:38 euskaltel kernel: [    0.493542] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493545] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493548] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Jan 17 01:00:38 euskaltel kernel: [    0.493551] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Jan 17 01:00:38 euskaltel kernel: [    0.493554] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Jan 17 01:00:38 euskaltel kernel: [    0.493557] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493565] pci 0000:00:04.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493570] pci 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493575] pci 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493579] pci 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493582] bus: 00 index 0 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493584] bus: 00 index 1 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493586] bus: 01 index 0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.493588] bus: 01 index 1 mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493590] bus: 01 index 2 mmio: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493592] bus: 01 index 3 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493594] bus: 01 index 4 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493596] bus: 02 index 0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.493598] bus: 02 index 1 mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493600] bus: 02 index 2 mmio: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493602] bus: 02 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493604] bus: 03 index 0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493606] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493608] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493610] bus: 03 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493612] bus: 04 index 0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493614] bus: 04 index 1 mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493616] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493617] bus: 04 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493627] NET: Registered protocol family 2
Jan 17 01:00:38 euskaltel kernel: [    0.493763] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494036] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494820] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.495192] TCP: Hash tables configured (established 131072 bind 65536)
Jan 17 01:00:38 euskaltel kernel: [    0.495194] TCP reno registered
Jan 17 01:00:38 euskaltel kernel: [    0.495327] NET: Registered protocol family 1
Jan 17 01:00:38 euskaltel kernel: [    0.495434] checking if image is initramfs... it is
Jan 17 01:00:38 euskaltel kernel: [    1.115818] Freeing initrd memory: 7960k freed
Jan 17 01:00:38 euskaltel kernel: [    1.116448] audit: initializing netlink socket (disabled)
Jan 17 01:00:38 euskaltel kernel: [    1.116461] type=2000 audit(1263686417.116:1): initialized
Jan 17 01:00:38 euskaltel kernel: [    1.121466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 17 01:00:38 euskaltel kernel: [    1.123323] VFS: Disk quotas dquot_6.5.1
Jan 17 01:00:38 euskaltel kernel: [    1.123393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 17 01:00:38 euskaltel kernel: [    1.123487] msgmni has been set to 1761
Jan 17 01:00:38 euskaltel kernel: [    1.123588] io scheduler noop registered
Jan 17 01:00:38 euskaltel kernel: [    1.123590] io scheduler anticipatory registered
Jan 17 01:00:38 euskaltel kernel: [    1.123592] io scheduler deadline registered
Jan 17 01:00:38 euskaltel kernel: [    1.123602] io scheduler cfq registered (default)
Jan 17 01:00:38 euskaltel kernel: [    1.123635] pci 0000:00:00.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136045] pci 0000:00:04.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136061] pci 0000:00:05.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136087] pci 0000:00:07.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136101] pci 0000:00:08.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136115] pci 0000:00:08.1: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136130] pci 0000:00:09.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136144] pci 0000:00:0b.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136159] pci 0000:00:0c.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136173] pci 0000:00:0d.0: Boot video device
Jan 17 01:00:38 euskaltel kernel: [    1.136260] pcieport-driver 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136282] pcieport-driver 0000:00:09.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136300] pci_express 0000:00:09.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136332] pci_express 0000:00:09.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136386] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136407] pcieport-driver 0000:00:0b.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136422] pci_express 0000:00:0b.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136451] pci_express 0000:00:0b.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136504] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136524] pcieport-driver 0000:00:0c.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136539] pci_express 0000:00:0c.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136569] pci_express 0000:00:0c.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136783] isapnp: Scanning for PnP cards...
Jan 17 01:00:38 euskaltel kernel: [    1.489432] isapnp: No Plug & Play device found
Jan 17 01:00:38 euskaltel kernel: [    1.519451] hpet_resources: 0xfeff0000 is busy
Jan 17 01:00:38 euskaltel kernel: [    1.519522] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 17 01:00:38 euskaltel kernel: [    1.521642] brd: module loaded
Jan 17 01:00:38 euskaltel kernel: [    1.521708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 17 01:00:38 euskaltel kernel: [    1.521800] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 17 01:00:38 euskaltel kernel: [    1.522162] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 17 01:00:38 euskaltel kernel: [    1.522166] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 17 01:00:38 euskaltel kernel: [    1.522464] mice: PS/2 mouse device common for all mice
Jan 17 01:00:38 euskaltel kernel: [    1.522576] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jan 17 01:00:38 euskaltel kernel: [    1.522610] rtc0: alarms up to one year, y3k, hpet irqs
Jan 17 01:00:38 euskaltel kernel: [    1.522699] EISA: Probing bus 0 at eisa.0
Jan 17 01:00:38 euskaltel kernel: [    1.522704] Cannot allocate resource for EISA slot 1
Jan 17 01:00:38 euskaltel kernel: [    1.522707] Cannot allocate resource for EISA slot 2
Jan 17 01:00:38 euskaltel kernel: [    1.522720] Cannot allocate resource for EISA slot 8
Jan 17 01:00:38 euskaltel kernel: [    1.522722] EISA: Detected 0 cards.
Jan 17 01:00:38 euskaltel kernel: [    1.522725] cpuidle: using governor ladder
Jan 17 01:00:38 euskaltel kernel: [    1.522727] cpuidle: using governor menu
Jan 17 01:00:38 euskaltel kernel: [    1.523155] TCP cubic registered
Jan 17 01:00:38 euskaltel kernel: [    1.523179] Using IPI No-Shortcut mode
Jan 17 01:00:38 euskaltel kernel: [    1.523328] registered taskstats version 1
Jan 17 01:00:38 euskaltel kernel: [    1.523443]   Magic number: 10:203:1
Jan 17 01:00:38 euskaltel kernel: [    1.523450] tty ttye9: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523461] tty ttybc: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523652] rtc_cmos 00:05: setting system clock to 2010-01-17 00:00:18 UTC (1263686418)
Jan 17 01:00:38 euskaltel kernel: [    1.523655] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 17 01:00:38 euskaltel kernel: [    1.523657] EDD information not available.
Jan 17 01:00:38 euskaltel kernel: [    1.524041] Freeing unused kernel memory: 428k freed
Jan 17 01:00:38 euskaltel kernel: [    1.524109] Write protecting the kernel text: 2588k
Jan 17 01:00:38 euskaltel kernel: [    1.524147] Write protecting the kernel read-only data: 940k
Jan 17 01:00:38 euskaltel kernel: [    1.544813] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 17 01:00:38 euskaltel kernel: [    1.744060] fuse init (API version 7.9)
Jan 17 01:00:38 euskaltel kernel: [    1.862062] fan PNP0C0B:00: registered as cooling_device0
Jan 17 01:00:38 euskaltel kernel: [    1.862067] ACPI: Fan [FAN] (on)
Jan 17 01:00:38 euskaltel kernel: [    1.868784] processor ACPI0007:00: registered as cooling_device1
Jan 17 01:00:38 euskaltel kernel: [    1.870876] ACPI: Expecting a [Reference] package element, found type 0
Jan 17 01:00:38 euskaltel kernel: [    1.871083] thermal LNXTHERM:01: registered as thermal_zone0
Jan 17 01:00:38 euskaltel kernel: [    1.871449] ACPI: Thermal Zone [THRM] (30 C)
Jan 17 01:00:38 euskaltel kernel: [    2.744077] usbcore: registered new interface driver usbfs
Jan 17 01:00:38 euskaltel kernel: [    2.744101] usbcore: registered new interface driver hub
Jan 17 01:00:38 euskaltel kernel: [    2.752175] No dock devices found.
Jan 17 01:00:38 euskaltel kernel: [    2.784050] usbcore: registered new device driver usb
Jan 17 01:00:38 euskaltel kernel: [    2.809697] SCSI subsystem initialized
Jan 17 01:00:38 euskaltel kernel: [    2.809760] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jan 17 01:00:38 euskaltel kernel: [    2.810181] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810191] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810196] forcedeth 0000:00:07.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    2.814686] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 17 01:00:38 euskaltel kernel: [    2.831542] libata version 3.00 loaded.
Jan 17 01:00:38 euskaltel kernel: [    3.328497] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:72:a9:fe:35
Jan 17 01:00:38 euskaltel kernel: [    3.328502] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Jan 17 01:00:38 euskaltel kernel: [    3.328958] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328970] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328984] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.328987] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.329023] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Jan 17 01:00:38 euskaltel kernel: [    3.329045] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Jan 17 01:00:38 euskaltel kernel: [    3.386211] usb usb1: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.386319] hub 1-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.386328] hub 1-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.592901] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592911] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 20 (level, low) -> IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592921] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592923] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.592944] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Jan 17 01:00:38 euskaltel kernel: [    3.592966] ehci_hcd 0000:00:02.1: debug port 1
Jan 17 01:00:38 euskaltel kernel: [    3.592970] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 17 01:00:38 euskaltel kernel: [    3.592984] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
Jan 17 01:00:38 euskaltel kernel: [    3.604016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 17 01:00:38 euskaltel kernel: [    3.604090] usb usb2: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.604113] hub 2-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.604120] hub 2-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.817083] sata_nv 0000:00:08.0: version 3.5
Jan 17 01:00:38 euskaltel kernel: [    3.817493] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817503] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817543] sata_nv 0000:00:08.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.820082] scsi0 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821181] scsi1 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821357] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Jan 17 01:00:38 euskaltel kernel: [    3.821360] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.076014] usb 2-8: new high speed USB device using ehci_hcd and address 3
Jan 17 01:00:38 euskaltel kernel: [    4.608032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    4.616299] ata2.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.616302] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 17 01:00:38 euskaltel kernel: [    4.632527] ata2.00: configured for UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.632609] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    4.633103] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633108] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633148] sata_nv 0000:00:08.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    4.633465] scsi2 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633673] scsi3 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633831] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.633834] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.763877] usb 2-8: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    5.072017] usb 1-2: new full speed USB device using ohci_hcd and address 2
Jan 17 01:00:38 euskaltel kernel: [    5.100033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    5.108119] ata3.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.124122] ata3.00: configured for UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.293649] usb 1-2: configuration #1 chosen from 2 choices
Jan 17 01:00:38 euskaltel kernel: [    5.312194] usbcore: registered new interface driver libusual
Jan 17 01:00:38 euskaltel kernel: [    5.324111] Initializing USB Mass Storage driver...
Jan 17 01:00:38 euskaltel kernel: [    5.325593] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 17 01:00:38 euskaltel kernel: [    5.325675] usbcore: registered new interface driver usb-storage
Jan 17 01:00:38 euskaltel kernel: [    5.325678] USB Mass Storage support registered.
Jan 17 01:00:38 euskaltel kernel: [    5.325753] usb-storage: device found at 3
Jan 17 01:00:38 euskaltel kernel: [    5.325754] usb-storage: waiting for device to settle before scanning
Jan 17 01:00:38 euskaltel kernel: [    5.334886] scsi 1:0:0:0: Attached scsi generic sg0 type 0
Jan 17 01:00:38 euskaltel kernel: [    5.449650] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    5.449776] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Jan 17 01:00:38 euskaltel kernel: [    5.449816] pata_amd 0000:00:06.0: version 0.3.10
Jan 17 01:00:38 euskaltel kernel: [    5.449860] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.450312] scsi5 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.450553] scsi6 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.451328] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 17 01:00:38 euskaltel kernel: [    5.451332] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 17 01:00:38 euskaltel kernel: [    5.614957] ata6: port disabled. ignoring.
Jan 17 01:00:38 euskaltel kernel: [    5.656068] Driver 'sd' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.656157] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656171] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656173] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656192] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656251] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656261] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656264] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656282] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656285]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.679675]  sda1 sda2 < sda5 >
Jan 17 01:00:38 euskaltel kernel: [    5.705190] sd 1:0:0:0: [sda] Attached SCSI disk
Jan 17 01:00:38 euskaltel kernel: [    5.717880] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 17 01:00:38 euskaltel kernel: [    5.717885] Uniform CD-ROM driver Revision: 3.20
Jan 17 01:00:38 euskaltel kernel: [    5.717972] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 17 01:00:38 euskaltel kernel: [    5.869216] PM: Starting manual resume from disk
Jan 17 01:00:38 euskaltel kernel: [    5.869219] PM: Resume from partition 8:5
Jan 17 01:00:38 euskaltel kernel: [    5.869221] PM: Checking hibernation image.
Jan 17 01:00:38 euskaltel kernel: [    5.869321] PM: Resume from disk failed.
Jan 17 01:00:38 euskaltel kernel: [    5.923899] kjournald starting.  Commit interval 5 seconds
Jan 17 01:00:38 euskaltel kernel: [    5.923910] EXT3-fs: mounted filesystem with ordered data mode.
Jan 17 01:00:38 euskaltel kernel: [   10.324166] usb-storage: device scan complete
Jan 17 01:00:38 euskaltel kernel: [   10.330532] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Jan 17 01:00:38 euskaltel kernel: [   10.331710] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 17 01:00:38 euskaltel kernel: [   10.331831] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 17 01:00:38 euskaltel kernel: [   12.116177] udevd version 124 started
Jan 17 01:00:38 euskaltel kernel: [   12.580180] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Jan 17 01:00:38 euskaltel kernel: [   12.580209] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
Jan 17 01:00:38 euskaltel kernel: [   13.024208] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 17 01:00:38 euskaltel kernel: [   13.040031] ACPI: Power Button (FF) [PWRF]
Jan 17 01:00:38 euskaltel kernel: [   13.040103] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Jan 17 01:00:38 euskaltel kernel: [   13.056033] ACPI: Power Button (CM) [PWRB]
Jan 17 01:00:38 euskaltel kernel: [   13.064162] ACPI: WMI: Mapper loaded
Jan 17 01:00:38 euskaltel kernel: [   13.984598] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984604] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984631] HDA Intel 0000:00:05.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   15.208291] eth1: register 'cdc_ether' at usb-0000:00:02.0-2, CDC Ethernet Device, 00:18:68:0a:59:75
Jan 17 01:00:38 euskaltel kernel: [   15.208311] usbcore: registered new interface driver cdc_ether
Jan 17 01:00:38 euskaltel kernel: [   15.366813] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 17 01:00:38 euskaltel kernel: [   15.393091] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 17 01:00:38 euskaltel kernel: [   15.457623] Linux agpgart interface v0.103
Jan 17 01:00:38 euskaltel kernel: [   15.638236] nvidia: module license 'NVIDIA' taints kernel.
Jan 17 01:00:38 euskaltel kernel: [   16.015092] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015098] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015105] nvidia 0000:00:0d.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   16.015355] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
Jan 17 01:00:38 euskaltel kernel: [   16.140880] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jan 17 01:00:38 euskaltel kernel: [   16.823744] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jan 17 01:00:38 euskaltel kernel: [   17.178460] udev: renamed network interface eth1 to eth2
Jan 17 01:00:38 euskaltel kernel: [   18.116894] lp: driver loaded but no devices found
Jan 17 01:00:38 euskaltel kernel: [   18.320383] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
Jan 17 01:00:38 euskaltel kernel: [   18.870393] EXT3 FS on sda1, internal journal
Jan 17 01:00:38 euskaltel kernel: [   20.073620] type=1505 audit(1263686437.081:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4096
Jan 17 01:00:38 euskaltel kernel: [   20.259552] type=1505 audit(1263686437.265:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.259778] type=1505 audit(1263686437.265:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.415348] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 17 01:00:38 euskaltel kernel: [   21.109118] powernow-k8: Found 1 AMD Athlon(tm) Processor LE-1600 processors (1 cpu cores) (version 2.20.00)
Jan 17 01:00:38 euskaltel kernel: [   21.109155] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
Jan 17 01:00:38 euskaltel kernel: [   21.109157] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
Jan 17 01:00:38 euskaltel kernel: [   21.109159] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
Jan 17 01:00:38 euskaltel kernel: [   21.109161] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jan 17 01:00:38 euskaltel kernel: [   21.923180] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 17 01:00:46 euskaltel kernel: [   29.634910] ppdev: user-space parallel port driver
Jan 17 01:00:50 euskaltel kernel: [   33.633134] eth0: no link during initialization.
Jan 17 01:00:51 euskaltel kernel: [   34.500016] Clocksource tsc unstable (delta = -90874311 ns)
Jan 17 01:00:55 euskaltel kernel: [   38.516037] NET: Registered protocol family 17
Jan 17 01:00:59 euskaltel kernel: [   42.926947] NET: Registered protocol family 10
Jan 17 01:00:59 euskaltel kernel: [   42.928576] lo: Disabled Privacy Extensions
Jan 17 01:00:59 euskaltel kernel: [   42.929484] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 17 01:01:10 euskaltel kernel: [   53.888014] eth2: no IPv6 routers present
```

```
Jan 17 01:00:38 euskaltel syslogd 1.5.0#2ubuntu6: restart.
Jan 17 01:00:38 euskaltel kernel: Inspecting /boot/System.map-2.6.27-16-generic
Jan 17 01:00:38 euskaltel kernel: Cannot find map file.
Jan 17 01:00:38 euskaltel kernel: Loaded 67477 symbols from 83 modules.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Linux version 2.6.27-16-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Dec 1 17:56:54 UTC 2009 (Ubuntu 2.6.27-16.44-generic)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] DMI 2.5 present.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] kernel direct mapping tables up to 37ee0000 @ 10000-16000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] RAMDISK: 37709000 - 37ecf0f3
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: RSDT 37EE3000, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACP 37EE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080609]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: DSDT 37EE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: FACS 37EE0000, 0040
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: SSDT 37EEA000, 0115 (r1 PTLTD  POWERNOW        1  LTP        1)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET 37EEA140, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA       98)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: MCFG 37EEA180, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: APIC 37EE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA        0)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 0MB HIGHMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] 894MB LOWMEM available.
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   mapped low ram: 0 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   low ram: 00000000 - 37ee0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   bootmap 00012000 - 00018fdc
Jan 17 01:00:38 euskaltel kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ee0000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #4 [0037709000 - 0037ecf0f3]          RAMDISK ==> [0037709000 - 0037ecf0f3]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jan 17 01:00:38 euskaltel kernel: [    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Zone PFN ranges:
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal   0x00001000 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   HighMem  0x00037ee0 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Movable zone start PFN for each node
Jan 17 01:00:38 euskaltel kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan 17 01:00:38 euskaltel kernel: [    0.000000]     0: 0x00000100 -> 0x00037ee0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] On node 0 totalpages: 228975
Jan 17 01:00:38 euskaltel kernel: [    0.000000] free_area_init_node: node 0, pgdat c048e700, node_mem_map c1000240
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   DMA zone: 3947 pages, LIFO batch:0
Jan 17 01:00:38 euskaltel kernel: [    0.000000]   Normal zone: 223014 pages, LIFO batch:31
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jan 17 01:00:38 euskaltel kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ14 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: IRQ15 used by override.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 17 01:00:38 euskaltel kernel: [    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jan 17 01:00:38 euskaltel kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226961
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Kernel command line: root=UUID=f825bb92-55a9-4133-bbf2-a7298808771e ro quiet splash 
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Initializing CPU#0
Jan 17 01:00:38 euskaltel kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jan 17 01:00:38 euskaltel kernel: [    0.000000] TSC: using PIT calibration value
Jan 17 01:00:38 euskaltel kernel: [    0.000000] Detected 2210.001 MHz processor.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Console: colour VGA+ 80x25
Jan 17 01:00:38 euskaltel kernel: [    0.004000] console [tty0] enabled
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Memory: 893820k/916352k available (2585k kernel code, 21936k reserved, 1164k data, 428k init, 0k highmem)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] virtual kernel memory layout:
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf7ee0000   ( 894 MB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .data : 0xc03864c8 - 0xc04a9680   (1164 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000]       .text : 0xc0100000 - 0xc03864c8   (2585 kB)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 17 01:00:38 euskaltel kernel: [    0.004000] hpet clockevent registered
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.00 BogoMIPS (lpj=8840004)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Security Framework initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] SELinux:  Disabled at boot.
Jan 17 01:00:38 euskaltel kernel: [    0.004000] AppArmor: AppArmor initialized
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Mount-cache hash table entries: 512
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys ns
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys cpuacct
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Initializing cgroup subsys memory
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Jan 17 01:00:38 euskaltel kernel: [    0.004000] using C1E aware idle routine
Jan 17 01:00:38 euskaltel kernel: [    0.004000] Checking 'hlt' instruction... OK.
Jan 17 01:00:38 euskaltel kernel: [    0.016301] SMP alternatives: switching to UP code
Jan 17 01:00:38 euskaltel kernel: [    0.020009] ACPI: Core revision 20080609
Jan 17 01:00:38 euskaltel kernel: [    0.022070] ACPI: Checking initramfs for custom DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.328299] ENABLING IO-APIC IRQs
Jan 17 01:00:38 euskaltel kernel: [    0.328524] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 17 01:00:38 euskaltel kernel: [    0.370956] CPU0: AMD Athlon(tm) Processor LE-1600 stepping 03
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Brought up 1 CPUs
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Total of 1 processors activated (4420.00 BogoMIPS).
Jan 17 01:00:38 euskaltel kernel: [    0.372023] CPU0 attaching NULL sched-domain.
Jan 17 01:00:38 euskaltel kernel: [    0.372023] net_namespace: 840 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Booting paravirtualized kernel on bare hardware
Jan 17 01:00:38 euskaltel kernel: [    0.372023] Time:  0:00:17  Date: 01/17/10
Jan 17 01:00:38 euskaltel kernel: [    0.372023] NET: Registered protocol family 16
Jan 17 01:00:38 euskaltel kernel: [    0.372023] EISA bus registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: bus type pci registered
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: MCFG area at f0000000 reserved in E820
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using MMCONFIG for extended config space
Jan 17 01:00:38 euskaltel kernel: [    0.372023] PCI: Using configuration type 1 for base access
Jan 17 01:00:38 euskaltel kernel: [    0.372023] ACPI: EC: Look up EC in DSDT
Jan 17 01:00:38 euskaltel kernel: [    0.379182] ACPI: Interpreter enabled
Jan 17 01:00:38 euskaltel kernel: [    0.379185] ACPI: (supports S0 S3 S4 S5)
Jan 17 01:00:38 euskaltel kernel: [    0.379199] ACPI: Using IOAPIC for interrupt routing
Jan 17 01:00:38 euskaltel kernel: [    0.389348] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 17 01:00:38 euskaltel kernel: [    0.389538] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
Jan 17 01:00:38 euskaltel kernel: [    0.389570] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389580] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
Jan 17 01:00:38 euskaltel kernel: [    0.389584] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
Jan 17 01:00:38 euskaltel kernel: [    0.389607] pci 0000:00:01.1: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389612] pci 0000:00:01.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389652] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.389676] pci 0000:00:02.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389678] pci 0000:00:02.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389680] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389683] pci 0000:00:02.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389701] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
Jan 17 01:00:38 euskaltel kernel: [    0.389731] pci 0000:00:02.1: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389732] pci 0000:00:02.1: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389734] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389738] pci 0000:00:02.1: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389790] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
Jan 17 01:00:38 euskaltel kernel: [    0.389820] pci 0000:00:05.0: PME# supported from D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389823] pci 0000:00:05.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389850] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
Jan 17 01:00:38 euskaltel kernel: [    0.389884] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389888] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
Jan 17 01:00:38 euskaltel kernel: [    0.389914] pci 0000:00:07.0: supports D1
Jan 17 01:00:38 euskaltel kernel: [    0.389916] pci 0000:00:07.0: supports D2
Jan 17 01:00:38 euskaltel kernel: [    0.389918] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.389922] pci 0000:00:07.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.389937] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
Jan 17 01:00:38 euskaltel kernel: [    0.389941] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
Jan 17 01:00:38 euskaltel kernel: [    0.389944] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
Jan 17 01:00:38 euskaltel kernel: [    0.389948] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
Jan 17 01:00:38 euskaltel kernel: [    0.389951] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
Jan 17 01:00:38 euskaltel kernel: [    0.389955] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
Jan 17 01:00:38 euskaltel kernel: [    0.389985] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
Jan 17 01:00:38 euskaltel kernel: [    0.389989] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
Jan 17 01:00:38 euskaltel kernel: [    0.389992] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
Jan 17 01:00:38 euskaltel kernel: [    0.389996] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
Jan 17 01:00:38 euskaltel kernel: [    0.389999] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
Jan 17 01:00:38 euskaltel kernel: [    0.390003] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390052] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390055] pci 0000:00:09.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390084] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390087] pci 0000:00:0b.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390115] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 17 01:00:38 euskaltel kernel: [    0.390118] pci 0000:00:0c.0: PME# disabled
Jan 17 01:00:38 euskaltel kernel: [    0.390129] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390134] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390139] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390144] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390248] pci 0000:00:04.0: transparent bridge
Jan 17 01:00:38 euskaltel kernel: [    0.390251] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.390254] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390257] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390290] PCI: bridge 0000:00:09.0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.390293] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390296] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390329] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390331] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390335] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390367] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.390369] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.390381] bus 00 -> node 0
Jan 17 01:00:38 euskaltel kernel: [    0.390389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.390753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jan 17 01:00:38 euskaltel kernel: [    0.442082] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442278] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442472] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442666] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.442860] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443054] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443248] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443442] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.443639] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.443832] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444034] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444235] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Jan 17 01:00:38 euskaltel kernel: [    0.444430] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.444624] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.444820] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445019] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445214] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.445410] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445609] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Jan 17 01:00:38 euskaltel kernel: [    0.445853] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446091] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446327] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446563] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.446799] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447036] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447272] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447508] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.447744] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.447984] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448231] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448468] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.448706] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.448943] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449180] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Jan 17 01:00:38 euskaltel kernel: [    0.449417] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449655] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Jan 17 01:00:38 euskaltel kernel: [    0.449892] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450128] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
Jan 17 01:00:38 euskaltel kernel: [    0.450292] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 17 01:00:38 euskaltel kernel: [    0.450319] pnp: PnP ACPI init
Jan 17 01:00:38 euskaltel kernel: [    0.450325] ACPI: bus type pnp registered
Jan 17 01:00:38 euskaltel kernel: [    0.455979] pnp: PnP ACPI: found 12 devices
Jan 17 01:00:38 euskaltel kernel: [    0.455981] ACPI: ACPI bus type pnp unregistered
Jan 17 01:00:38 euskaltel kernel: [    0.455983] PnPBIOS: Disabled by ACPI PNP
Jan 17 01:00:38 euskaltel kernel: [    0.456252] PCI: Using ACPI for IRQ routing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 8
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NET: Registered protocol family 20
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel: Initializing
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  domain hash size = 128
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 17 01:00:38 euskaltel kernel: [    0.456336] NetLabel:  unlabeled traffic allowed by default
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jan 17 01:00:38 euskaltel kernel: [    0.456336] hpet0: 3 32-bit timers, 25000000 Hz
Jan 17 01:00:38 euskaltel kernel: [    0.457996] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 17 01:00:38 euskaltel kernel: [    0.457998]    actual entries 65620
Jan 17 01:00:38 euskaltel kernel: [    0.458152] AppArmor: AppArmor Filesystem Enabled
Jan 17 01:00:38 euskaltel kernel: [    0.458176] ACPI: RTC can wake from S4
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1000-0x107f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1400-0x147f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1800-0x187f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2000-0x207f has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:01: ioport range 0x2080-0x20ff has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:02: ioport range 0x295-0x314 has been reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0x38000000-0x3fffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.458181] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be reserved
Jan 17 01:00:38 euskaltel kernel: [    0.460042] Switched to high resolution mode on CPU 0
Jan 17 01:00:38 euskaltel kernel: [    0.493510] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
Jan 17 01:00:38 euskaltel kernel: [    0.493513] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
Jan 17 01:00:38 euskaltel kernel: [    0.493516] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493520] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jan 17 01:00:38 euskaltel kernel: [    0.493524] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
Jan 17 01:00:38 euskaltel kernel: [    0.493527] pci 0000:00:09.0:   IO window: 0xa000-0xafff
Jan 17 01:00:38 euskaltel kernel: [    0.493530] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
Jan 17 01:00:38 euskaltel kernel: [    0.493533] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493536] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
Jan 17 01:00:38 euskaltel kernel: [    0.493539] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
Jan 17 01:00:38 euskaltel kernel: [    0.493542] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493545] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Jan 17 01:00:38 euskaltel kernel: [    0.493548] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
Jan 17 01:00:38 euskaltel kernel: [    0.493551] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
Jan 17 01:00:38 euskaltel kernel: [    0.493554] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
Jan 17 01:00:38 euskaltel kernel: [    0.493557] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Jan 17 01:00:38 euskaltel kernel: [    0.493565] pci 0000:00:04.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493570] pci 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493575] pci 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493579] pci 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    0.493582] bus: 00 index 0 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493584] bus: 00 index 1 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493586] bus: 01 index 0 io port: [b000, bfff]
Jan 17 01:00:38 euskaltel kernel: [    0.493588] bus: 01 index 1 mmio: [fd800000, fd8fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493590] bus: 01 index 2 mmio: [fdf00000, fdffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493592] bus: 01 index 3 io port: [0, ffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493594] bus: 01 index 4 mmio: [0, ffffffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493596] bus: 02 index 0 io port: [a000, afff]
Jan 17 01:00:38 euskaltel kernel: [    0.493598] bus: 02 index 1 mmio: [fde00000, fdefffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493600] bus: 02 index 2 mmio: [fdd00000, fddfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493602] bus: 02 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493604] bus: 03 index 0 io port: [9000, 9fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493606] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493608] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493610] bus: 03 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493612] bus: 04 index 0 io port: [8000, 8fff]
Jan 17 01:00:38 euskaltel kernel: [    0.493614] bus: 04 index 1 mmio: [fda00000, fdafffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493616] bus: 04 index 2 mmio: [fd900000, fd9fffff]
Jan 17 01:00:38 euskaltel kernel: [    0.493617] bus: 04 index 3 mmio: [0, 0]
Jan 17 01:00:38 euskaltel kernel: [    0.493627] NET: Registered protocol family 2
Jan 17 01:00:38 euskaltel kernel: [    0.493763] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494036] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.494820] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 17 01:00:38 euskaltel kernel: [    0.495192] TCP: Hash tables configured (established 131072 bind 65536)
Jan 17 01:00:38 euskaltel kernel: [    0.495194] TCP reno registered
Jan 17 01:00:38 euskaltel kernel: [    0.495327] NET: Registered protocol family 1
Jan 17 01:00:38 euskaltel kernel: [    0.495434] checking if image is initramfs... it is
Jan 17 01:00:38 euskaltel kernel: [    1.115818] Freeing initrd memory: 7960k freed
Jan 17 01:00:38 euskaltel kernel: [    1.116448] audit: initializing netlink socket (disabled)
Jan 17 01:00:38 euskaltel kernel: [    1.116461] type=2000 audit(1263686417.116:1): initialized
Jan 17 01:00:38 euskaltel kernel: [    1.121466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 17 01:00:38 euskaltel kernel: [    1.123323] VFS: Disk quotas dquot_6.5.1
Jan 17 01:00:38 euskaltel kernel: [    1.123393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 17 01:00:38 euskaltel kernel: [    1.123487] msgmni has been set to 1761
Jan 17 01:00:38 euskaltel kernel: [    1.123588] io scheduler noop registered
Jan 17 01:00:38 euskaltel kernel: [    1.123590] io scheduler anticipatory registered
Jan 17 01:00:38 euskaltel kernel: [    1.123592] io scheduler deadline registered
Jan 17 01:00:38 euskaltel kernel: [    1.123602] io scheduler cfq registered (default)
Jan 17 01:00:38 euskaltel kernel: [    1.123635] pci 0000:00:00.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136045] pci 0000:00:04.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136061] pci 0000:00:05.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136087] pci 0000:00:07.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136101] pci 0000:00:08.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136115] pci 0000:00:08.1: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136130] pci 0000:00:09.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136144] pci 0000:00:0b.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136159] pci 0000:00:0c.0: Enabling HT MSI Mapping
Jan 17 01:00:38 euskaltel kernel: [    1.136173] pci 0000:00:0d.0: Boot video device
Jan 17 01:00:38 euskaltel kernel: [    1.136260] pcieport-driver 0000:00:09.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136282] pcieport-driver 0000:00:09.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136300] pci_express 0000:00:09.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136332] pci_express 0000:00:09.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136386] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136407] pcieport-driver 0000:00:0b.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136422] pci_express 0000:00:0b.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136451] pci_express 0000:00:0b.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136504] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    1.136524] pcieport-driver 0000:00:0c.0: found MSI capability
Jan 17 01:00:38 euskaltel kernel: [    1.136539] pci_express 0000:00:0c.0:pcie00: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136569] pci_express 0000:00:0c.0:pcie03: allocate port service
Jan 17 01:00:38 euskaltel kernel: [    1.136783] isapnp: Scanning for PnP cards...
Jan 17 01:00:38 euskaltel kernel: [    1.489432] isapnp: No Plug & Play device found
Jan 17 01:00:38 euskaltel kernel: [    1.519451] hpet_resources: 0xfeff0000 is busy
Jan 17 01:00:38 euskaltel kernel: [    1.519522] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 17 01:00:38 euskaltel kernel: [    1.521642] brd: module loaded
Jan 17 01:00:38 euskaltel kernel: [    1.521708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 17 01:00:38 euskaltel kernel: [    1.521800] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 17 01:00:38 euskaltel kernel: [    1.522162] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 17 01:00:38 euskaltel kernel: [    1.522166] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 17 01:00:38 euskaltel kernel: [    1.522464] mice: PS/2 mouse device common for all mice
Jan 17 01:00:38 euskaltel kernel: [    1.522576] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jan 17 01:00:38 euskaltel kernel: [    1.522610] rtc0: alarms up to one year, y3k, hpet irqs
Jan 17 01:00:38 euskaltel kernel: [    1.522699] EISA: Probing bus 0 at eisa.0
Jan 17 01:00:38 euskaltel kernel: [    1.522704] Cannot allocate resource for EISA slot 1
Jan 17 01:00:38 euskaltel kernel: [    1.522707] Cannot allocate resource for EISA slot 2
Jan 17 01:00:38 euskaltel kernel: [    1.522720] Cannot allocate resource for EISA slot 8
Jan 17 01:00:38 euskaltel kernel: [    1.522722] EISA: Detected 0 cards.
Jan 17 01:00:38 euskaltel kernel: [    1.522725] cpuidle: using governor ladder
Jan 17 01:00:38 euskaltel kernel: [    1.522727] cpuidle: using governor menu
Jan 17 01:00:38 euskaltel kernel: [    1.523155] TCP cubic registered
Jan 17 01:00:38 euskaltel kernel: [    1.523179] Using IPI No-Shortcut mode
Jan 17 01:00:38 euskaltel kernel: [    1.523328] registered taskstats version 1
Jan 17 01:00:38 euskaltel kernel: [    1.523443]   Magic number: 10:203:1
Jan 17 01:00:38 euskaltel kernel: [    1.523450] tty ttye9: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523461] tty ttybc: hash matches
Jan 17 01:00:38 euskaltel kernel: [    1.523652] rtc_cmos 00:05: setting system clock to 2010-01-17 00:00:18 UTC (1263686418)
Jan 17 01:00:38 euskaltel kernel: [    1.523655] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 17 01:00:38 euskaltel kernel: [    1.523657] EDD information not available.
Jan 17 01:00:38 euskaltel kernel: [    1.524041] Freeing unused kernel memory: 428k freed
Jan 17 01:00:38 euskaltel kernel: [    1.524109] Write protecting the kernel text: 2588k
Jan 17 01:00:38 euskaltel kernel: [    1.524147] Write protecting the kernel read-only data: 940k
Jan 17 01:00:38 euskaltel kernel: [    1.544813] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 17 01:00:38 euskaltel kernel: [    1.744060] fuse init (API version 7.9)
Jan 17 01:00:38 euskaltel kernel: [    1.862062] fan PNP0C0B:00: registered as cooling_device0
Jan 17 01:00:38 euskaltel kernel: [    1.862067] ACPI: Fan [FAN] (on)
Jan 17 01:00:38 euskaltel kernel: [    1.868784] processor ACPI0007:00: registered as cooling_device1
Jan 17 01:00:38 euskaltel kernel: [    1.870876] ACPI: Expecting a [Reference] package element, found type 0
Jan 17 01:00:38 euskaltel kernel: [    1.871083] thermal LNXTHERM:01: registered as thermal_zone0
Jan 17 01:00:38 euskaltel kernel: [    1.871449] ACPI: Thermal Zone [THRM] (30 C)
Jan 17 01:00:38 euskaltel kernel: [    2.744077] usbcore: registered new interface driver usbfs
Jan 17 01:00:38 euskaltel kernel: [    2.744101] usbcore: registered new interface driver hub
Jan 17 01:00:38 euskaltel kernel: [    2.752175] No dock devices found.
Jan 17 01:00:38 euskaltel kernel: [    2.784050] usbcore: registered new device driver usb
Jan 17 01:00:38 euskaltel kernel: [    2.809697] SCSI subsystem initialized
Jan 17 01:00:38 euskaltel kernel: [    2.809760] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jan 17 01:00:38 euskaltel kernel: [    2.810181] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810191] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [    2.810196] forcedeth 0000:00:07.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    2.814686] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 17 01:00:38 euskaltel kernel: [    2.831542] libata version 3.00 loaded.
Jan 17 01:00:38 euskaltel kernel: [    3.328497] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1d:72:a9:fe:35
Jan 17 01:00:38 euskaltel kernel: [    3.328502] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Jan 17 01:00:38 euskaltel kernel: [    3.328958] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328970] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [    3.328984] ohci_hcd 0000:00:02.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.328987] ohci_hcd 0000:00:02.0: OHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.329023] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Jan 17 01:00:38 euskaltel kernel: [    3.329045] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
Jan 17 01:00:38 euskaltel kernel: [    3.386211] usb usb1: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.386319] hub 1-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.386328] hub 1-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.592901] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592911] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 20 (level, low) -> IRQ 20
Jan 17 01:00:38 euskaltel kernel: [    3.592921] ehci_hcd 0000:00:02.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.592923] ehci_hcd 0000:00:02.1: EHCI Host Controller
Jan 17 01:00:38 euskaltel kernel: [    3.592944] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Jan 17 01:00:38 euskaltel kernel: [    3.592966] ehci_hcd 0000:00:02.1: debug port 1
Jan 17 01:00:38 euskaltel kernel: [    3.592970] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Jan 17 01:00:38 euskaltel kernel: [    3.592984] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
Jan 17 01:00:38 euskaltel kernel: [    3.604016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 17 01:00:38 euskaltel kernel: [    3.604090] usb usb2: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    3.604113] hub 2-0:1.0: USB hub found
Jan 17 01:00:38 euskaltel kernel: [    3.604120] hub 2-0:1.0: 10 ports detected
Jan 17 01:00:38 euskaltel kernel: [    3.817083] sata_nv 0000:00:08.0: version 3.5
Jan 17 01:00:38 euskaltel kernel: [    3.817493] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817503] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    3.817543] sata_nv 0000:00:08.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    3.820082] scsi0 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821181] scsi1 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    3.821357] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
Jan 17 01:00:38 euskaltel kernel: [    3.821360] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.076014] usb 2-8: new high speed USB device using ehci_hcd and address 3
Jan 17 01:00:38 euskaltel kernel: [    4.608032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    4.616299] ata2.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.616302] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 17 01:00:38 euskaltel kernel: [    4.632527] ata2.00: configured for UDMA/133
Jan 17 01:00:38 euskaltel kernel: [    4.632609] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    4.633103] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633108] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
Jan 17 01:00:38 euskaltel kernel: [    4.633148] sata_nv 0000:00:08.1: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    4.633465] scsi2 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633673] scsi3 : sata_nv
Jan 17 01:00:38 euskaltel kernel: [    4.633831] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.633834] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
Jan 17 01:00:38 euskaltel kernel: [    4.763877] usb 2-8: configuration #1 chosen from 1 choice
Jan 17 01:00:38 euskaltel kernel: [    5.072017] usb 1-2: new full speed USB device using ohci_hcd and address 2
Jan 17 01:00:38 euskaltel kernel: [    5.100033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 17 01:00:38 euskaltel kernel: [    5.108119] ata3.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.124122] ata3.00: configured for UDMA/100
Jan 17 01:00:38 euskaltel kernel: [    5.293649] usb 1-2: configuration #1 chosen from 2 choices
Jan 17 01:00:38 euskaltel kernel: [    5.312194] usbcore: registered new interface driver libusual
Jan 17 01:00:38 euskaltel kernel: [    5.324111] Initializing USB Mass Storage driver...
Jan 17 01:00:38 euskaltel kernel: [    5.325593] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 17 01:00:38 euskaltel kernel: [    5.325675] usbcore: registered new interface driver usb-storage
Jan 17 01:00:38 euskaltel kernel: [    5.325678] USB Mass Storage support registered.
Jan 17 01:00:38 euskaltel kernel: [    5.325753] usb-storage: device found at 3
Jan 17 01:00:38 euskaltel kernel: [    5.325754] usb-storage: waiting for device to settle before scanning
Jan 17 01:00:38 euskaltel kernel: [    5.334886] scsi 1:0:0:0: Attached scsi generic sg0 type 0
Jan 17 01:00:38 euskaltel kernel: [    5.449650] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
Jan 17 01:00:38 euskaltel kernel: [    5.449776] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Jan 17 01:00:38 euskaltel kernel: [    5.449816] pata_amd 0000:00:06.0: version 0.3.10
Jan 17 01:00:38 euskaltel kernel: [    5.449860] pata_amd 0000:00:06.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [    5.450312] scsi5 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.450553] scsi6 : pata_amd
Jan 17 01:00:38 euskaltel kernel: [    5.451328] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 17 01:00:38 euskaltel kernel: [    5.451332] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 17 01:00:38 euskaltel kernel: [    5.614957] ata6: port disabled. ignoring.
Jan 17 01:00:38 euskaltel kernel: [    5.656068] Driver 'sd' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.656157] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656171] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656173] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656192] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656251] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 17 01:00:38 euskaltel kernel: [    5.656261] sd 1:0:0:0: [sda] Write Protect is off
Jan 17 01:00:38 euskaltel kernel: [    5.656264] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 17 01:00:38 euskaltel kernel: [    5.656282] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 01:00:38 euskaltel kernel: [    5.656285]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jan 17 01:00:38 euskaltel kernel: [    5.679675]  sda1 sda2 < sda5 >
Jan 17 01:00:38 euskaltel kernel: [    5.705190] sd 1:0:0:0: [sda] Attached SCSI disk
Jan 17 01:00:38 euskaltel kernel: [    5.717880] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 17 01:00:38 euskaltel kernel: [    5.717885] Uniform CD-ROM driver Revision: 3.20
Jan 17 01:00:38 euskaltel kernel: [    5.717972] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 17 01:00:38 euskaltel kernel: [    5.869216] PM: Starting manual resume from disk
Jan 17 01:00:38 euskaltel kernel: [    5.869219] PM: Resume from partition 8:5
Jan 17 01:00:38 euskaltel kernel: [    5.869221] PM: Checking hibernation image.
Jan 17 01:00:38 euskaltel kernel: [    5.869321] PM: Resume from disk failed.
Jan 17 01:00:38 euskaltel kernel: [    5.923899] kjournald starting.  Commit interval 5 seconds
Jan 17 01:00:38 euskaltel kernel: [    5.923910] EXT3-fs: mounted filesystem with ordered data mode.
Jan 17 01:00:38 euskaltel kernel: [   10.324166] usb-storage: device scan complete
Jan 17 01:00:38 euskaltel kernel: [   10.330532] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Jan 17 01:00:38 euskaltel kernel: [   10.331710] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 17 01:00:38 euskaltel kernel: [   10.331831] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 17 01:00:38 euskaltel kernel: [   12.116177] udevd version 124 started
Jan 17 01:00:38 euskaltel kernel: [   12.580180] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Jan 17 01:00:38 euskaltel kernel: [   12.580209] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
Jan 17 01:00:38 euskaltel kernel: [   13.024208] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 17 01:00:38 euskaltel kernel: [   13.040031] ACPI: Power Button (FF) [PWRF]
Jan 17 01:00:38 euskaltel kernel: [   13.040103] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Jan 17 01:00:38 euskaltel kernel: [   13.056033] ACPI: Power Button (CM) [PWRB]
Jan 17 01:00:38 euskaltel kernel: [   13.064162] ACPI: WMI: Mapper loaded
Jan 17 01:00:38 euskaltel kernel: [   13.984598] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984604] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Jan 17 01:00:38 euskaltel kernel: [   13.984631] HDA Intel 0000:00:05.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   15.208291] eth1: register 'cdc_ether' at usb-0000:00:02.0-2, CDC Ethernet Device, 00:18:68:0a:59:75
Jan 17 01:00:38 euskaltel kernel: [   15.208311] usbcore: registered new interface driver cdc_ether
Jan 17 01:00:38 euskaltel kernel: [   15.366813] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 17 01:00:38 euskaltel kernel: [   15.393091] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 17 01:00:38 euskaltel kernel: [   15.457623] Linux agpgart interface v0.103
Jan 17 01:00:38 euskaltel kernel: [   15.638236] nvidia: module license 'NVIDIA' taints kernel.
Jan 17 01:00:38 euskaltel kernel: [   16.015092] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015098] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
Jan 17 01:00:38 euskaltel kernel: [   16.015105] nvidia 0000:00:0d.0: setting latency timer to 64
Jan 17 01:00:38 euskaltel kernel: [   16.015355] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
Jan 17 01:00:38 euskaltel kernel: [   16.140880] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jan 17 01:00:38 euskaltel kernel: [   16.823744] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jan 17 01:00:38 euskaltel kernel: [   17.178460] udev: renamed network interface eth1 to eth2
Jan 17 01:00:38 euskaltel kernel: [   18.116894] lp: driver loaded but no devices found
Jan 17 01:00:38 euskaltel kernel: [   18.320383] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
Jan 17 01:00:38 euskaltel kernel: [   18.870393] EXT3 FS on sda1, internal journal
Jan 17 01:00:38 euskaltel kernel: [   20.073620] type=1505 audit(1263686437.081:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4096
Jan 17 01:00:38 euskaltel kernel: [   20.259552] type=1505 audit(1263686437.265:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.259778] type=1505 audit(1263686437.265:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4101
Jan 17 01:00:38 euskaltel kernel: [   20.415348] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 17 01:00:38 euskaltel kernel: [   21.109118] powernow-k8: Found 1 AMD Athlon(tm) Processor LE-1600 processors (1 cpu cores) (version 2.20.00)
Jan 17 01:00:38 euskaltel kernel: [   21.109155] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
Jan 17 01:00:38 euskaltel kernel: [   21.109157] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
Jan 17 01:00:38 euskaltel kernel: [   21.109159] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
Jan 17 01:00:38 euskaltel kernel: [   21.109161] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jan 17 01:00:38 euskaltel kernel: [   21.923180] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped root privileges.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: avahi-daemon 0.6.23 starting up.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully called chroot().
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Successfully dropped remaining capabilities.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: No service file found in /etc/avahi/services.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Network interface enumeration completed.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 17 01:00:38 euskaltel avahi-daemon[4720]: Server startup complete. Host name is euskaltel.local. Local service cookie is 3919910173.
Jan 17 01:00:40 euskaltel avguard.bin[4798]: Info: Using library for dazuko version 3 
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: failed to register with Dazuko
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: termination of process 4807 (Guard scanner): connecting dazuko failed
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: On-Access protection is lost.
Jan 17 01:00:40 euskaltel avguard.bin[4805]: Warning: No dazuko module available, on-access protection disabled.
Jan 17 01:00:46 euskaltel kernel: [   29.634910] ppdev: user-space parallel port driver
Jan 17 01:00:49 euskaltel dhcdbd: Started up.
Jan 17 01:00:50 euskaltel acpid: client connected from 5167[111:123] 
Jan 17 01:00:50 euskaltel kernel: [   33.633134] eth0: no link during initialization.
Jan 17 01:00:51 euskaltel kernel: [   34.500016] Clocksource tsc unstable (delta = -90874311 ns)
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 104 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel last message repeated 135 times
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_keys: assertion `key_file != NULL' failed 
Jan 17 01:00:51 euskaltel gdm[5251]: GLib-CRITICAL: g_key_file_get_value: assertion `key_file != NULL' failed 
Jan 17 01:00:52 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:52 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
Jan 17 01:00:53 euskaltel /usr/sbin/cron[5347]: (CRON) INFO (pidfile fd = 3)
Jan 17 01:00:53 euskaltel /usr/sbin/cron[5348]: (CRON) STARTUP (fork ok)
Jan 17 01:00:53 euskaltel acpid: client connected from 5259[0:0] 
Jan 17 01:00:53 euskaltel /usr/sbin/cron[5348]: (CRON) INFO (Running @reboot jobs)
Jan 17 01:00:55 euskaltel kernel: [   38.516037] NET: Registered protocol family 17
Jan 17 01:00:58 euskaltel dhclient: DHCPREQUEST of 85.84.234.186 on eth2 to 255.255.255.255 port 67
Jan 17 01:00:58 euskaltel dhclient: DHCPACK of 85.84.234.186 from 10.77.128.1
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:58 euskaltel dhclient: bound to 85.84.234.186 -- renewal in 35752 seconds.
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.host_name
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_domain
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_servers
Jan 17 01:00:58 euskaltel dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.interface_mtu
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Withdrawing address record for 85.84.234.186 on eth2.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Interface eth2.IPv4 no longer relevant for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Joining mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: New relevant interface eth2.IPv4 for mDNS.
Jan 17 01:00:58 euskaltel avahi-daemon[4720]: Registering new address record for 85.84.234.186 on eth2.IPv4.
Jan 17 01:00:59 euskaltel kernel: [   42.926947] NET: Registered protocol family 10
Jan 17 01:00:59 euskaltel kernel: [   42.928576] lo: Disabled Privacy Extensions
Jan 17 01:00:59 euskaltel kernel: [   42.929484] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 17 01:01:00 euskaltel ntpdate[5551]: adjust time server 91.189.94.4 offset -0.147056 sec
Jan 17 01:01:01 euskaltel avahi-daemon[4720]: Registering new address record for fe80::218:68ff:fe0a:5975 on eth2.*.
Jan 17 01:01:10 euskaltel kernel: [   53.888014] eth2: no IPv6 routers present
Jan 17 01:10:02 euskaltel /USR/SBIN/CRON[5569]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:17:01 euskaltel /USR/SBIN/CRON[5651]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 17 01:20:01 euskaltel /USR/SBIN/CRON[5695]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:30:01 euskaltel /USR/SBIN/CRON[5778]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:40:01 euskaltel /USR/SBIN/CRON[5861]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 01:50:01 euskaltel /USR/SBIN/CRON[5944]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 02:00:01 euskaltel /USR/SBIN/CRON[6027]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 02:10:01 euskaltel /USR/SBIN/CRON[6110]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 17 02:17:01 euskaltel /USR/SBIN/CRON[6193]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 17 02:18:28 euskaltel init: tty4 main process (4296) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty5 main process (4297) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty2 main process (4304) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty3 main process (4305) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty6 main process (4306) killed by TERM signal
Jan 17 02:18:28 euskaltel init: tty1 main process (5457) killed by TERM signal
Jan 17 02:18:29 euskaltel acpid: client 5259[0:0] has disconnected 
Jan 17 02:18:29 euskaltel acpid: client 5259[0:0] has disconnected 
Jan 17 02:18:29 euskaltel avguard.bin[4805]: Info: service terminated. Shutting down
Jan 17 02:18:36 euskaltel avahi-daemon[4720]: Got SIGTERM, quitting.
Jan 17 02:18:36 euskaltel avahi-daemon[4720]: Leaving mDNS multicast group on interface eth2.IPv4 with address 85.84.234.186.
Jan 17 02:18:36 euskaltel exiting on signal 15
```

Why does this annoying anomaly happen? Virus (unlikely because I made a whole system scan less than a week ago)? Just the usual crazy Ubuntu bug, which was maybe even intended as feature? Has my PC (AMD Athlon 64) acquired life of its own?

The PC (cheapest in market here) has not a power switch, tough I guess I can always pull out the power plug but really I'd like it to sleep all the way until I click on the on/off button, as it used to.

Thanks in advance

Hmm!Strange...How would a OS boot itself?My best guess would be either a Wake on lan enabled lan card (or) a power fluctuation.Some machines when you plug the power cord into them,they power up.This may be the only reason if you have ruled out the WOL lan card.

---

### Post by lisati on 2010-01-17
> **dnvikram said:**
> Hmm!Strange...How would a OS boot itself?My best guess would be either a **Wake on lan** enabled lan card (or) a power fluctuation.Some machines when you plug the power cord into them,they power up.This may be the only reason if you have ruled out the WOL lan card.

Wake on Lan is what I was thinking too.

---

### Post by Maju on 2010-01-17
> Check your bios settings.

I will but never happened before the upgrade, so I doubt it's the case. Seems something related with Ibex' default configuration.

> a Wake on lan enabled lan card

Hmmm. I have only direct cable-modem, no LAN as far as I can tell. Anyhow, how can I check that? (I'll try but not sure).

> a power fluctuation

Can't be because it happens every night at exactly the same time (1:00:39 am). A power fluctuation would be random, right?

...

Checking the logs again, the first command seems:

Jan 17 01:00:38 euskaltel syslogd 1.5.0#2ubuntu6: restart.

It's like it has a programmed restart somehow.

---

### Post by lisati on 2010-01-17
> **Maju said:**
> 
Hmmm. I have only direct cable-modem, no LAN as far as I can tell. Anyhow, how can I check that? (I'll try but not sure).


How does your computer connect to your modem, by ethernet cable or by USB cable? If it's by ethernet cable, your system could be interpreting it as a LAN.

---

### Post by Maju on 2010-01-17
**USB cable**

I also checked the BIOS settings and they seem in default mode. 

I insist: only began happening after I upgraded to Intrepid Ibex. 

However there is something that has called my attention: instead of having a users menu button and then the shutdown button at the upper right corner, II has the shutdown feature in the users menu, which includes:

[LIST]
[*]guest session
[*]lock screen
[*]log out
[*]suspend
[*]hibernate
[*]restart
[*]**shutdown**
[/LIST]

I have been using this **shutdown** option to turn off the computer so far. 

What used to be the shutdown button in Hardy (top right corner), in Intepid gives only two options: **log out** and **switch user**. So far I haven't used it but a moment ago experimentally.

So I have found that, if I log out I have the option of shutting off or restarting from the E-Machines interface. And that is what I'm going to use tonight in the hope it works properly. 

More tomorrow and thanks for trying anyhow.

---

### Post by Maju on 2010-01-18
The workaround was effective: tonight the computer remained off for the whole night. 

However this is not a true solution or explanation, just a trick. I'd still like to know how to fix the matter properly: what in the Intrepid Ibex configuration is causing this anomaly? :-s

---

### Post by perspectoff on 2010-01-18
Does it watch porn sites on its own, late at night?

---

### Post by alwayshere on 2010-01-18
You have ghosts what you need to do is find a goat wait untill 12:50 then in the terminal put
--------------------------------------------
sudo apt-get install goatkill -drink -blood
--------------------------------------------

and wait till 12:58 and cut the goats throat and fill a cup with the blood 
and drink it at 1:00 on the dot .

then in terminal put

sudo apt-get installdrunk -blood

then  

sudo apt-get remove <ghost> --purge

And all should be sorted

---

### Post by stupor on 2010-01-20
By the time i drunk the blood it was 1.05am.
as you can guess it did not work for me ill try again tonight 
thanks for your help alwayshere.

---

### Post by dzon65 on 2010-01-20
You should go through your settings.It's probably set to wake on LAN.

---

### Post by Maju on 2010-01-27
> **perspectoff said:**
> Does it watch porn sites on its own, late at night?

No. It does nothing (except whatever the logs says it does, something about avahi daemon, whatever that is - look above). Just turns on and waits for me to log (or as I have typically done, turn it off angrily). 

I found a way around (logging off before turning the PC off) but hoped to be able to know why the computer turns itself on as never happened before the upgrade and Antivir (updated) says there's nothing odd.

---

### Post by Maju on 2010-01-27
> **dzon65 said:**
> You should go through your settings.It's probably set to wake on LAN.

Looks like a nice advise. But how can I access those settings? I can't find any menu that looks like "settings". I have checked everything I could imagine it could do anything.

---

### Post by t4thfavor on 2010-01-27
It's probably somebody who is on your segment of the cable broadcasting magicpackets from some sort of malware to wake up other unsuspecting hosts in an attempt to infect them. I worked for a school where a piece of software (malicious) would wake all the PC's every night, and attempt to infect them. 

I would suspect one of your neighbours who is also directly connected is rooted, and has no idea this is happening. Try unplugging your cable modem for a few nights, and see if it stops.

I would also recommend getting a nat router (cheapo) just to add that extra layer you currently do not have.

And Wake On Lan settings are in your BIOS you have to wait for the post screen and press whatever key it tells you to for setup, usually F2, Del, or F1.

---

### Post by Maju on 2010-02-03
> **t4thfavor said:**
> It's probably somebody who is on your segment of the cable broadcasting magicpackets from some sort of malware to wake up other unsuspecting hosts in an attempt to infect them. I worked for a school where a piece of software (malicious) would wake all the PC's every night, and attempt to infect them. 

I would suspect one of your neighbours who is also directly connected is rooted, and has no idea this is happening. Try unplugging your cable modem for a few nights, and see if it stops.

I would also recommend getting a nat router (cheapo) just to add that extra layer you currently do not have.

And Wake On Lan settings are in your BIOS you have to wait for the post screen and press whatever key it tells you to for setup, usually F2, Del, or F1.

Makes some sense, thanks. However I still find odd that it never did that when it was with Hardy, only after upgrade to Intrepid and the very same night after I did the upgrade.

Also, as I have said before, if I log out before shutting down the PC, then it does not happen: only if I shut it directly while still logged.

I checked the BIOS again and found **wake up on USB** and **wake up on PS2 enabled**. By the description these should only recover from S3 state (suspend, I understand) on key pressing. There is no wake up on LAN option anywhere (checked and rechecked all BIOS menus). 

However as the keyboard and mouse are connected by PS2 and only the modem uses USB I will cautionarily disable the wake up on USB feature. I still believe it should not start the PC in any case, as only the on/off main button should do that. 

Would it be the case that someone is "on my segment of the cable broadcasting magicpackets", then should it be someone accessing the same modem as I do or just any other customer from the same server? I ask because, in the first case, I should warn them that they might be infected by malware (only my apartment mates have access to this modem). In the second case, there'd be nothing I could do probably.

---

### Post by Maju on 2010-02-15
Seems that disabling the "wake up on USB" from BIOS settings worked. Thanks all and sorry for bothering you.

---

### Post by Bakerconspiracy on 2010-02-18
> **perspectoff said:**
> Does it watch porn sites on its own, late at night?

Haha I was thinking the same thing.

---

### Post by adouglasmhor on 2010-02-18
> **Maju said:**
> Seems that disabling the "wake up on USB" from BIOS settings worked. Thanks all and sorry for bothering you.

I don't think anyone thought you were bothering them. I am Glad you got it sorted.

---

### Post by El Zoido on 2010-02-18
Would still be interesting to find out what exactly is happening every night at that time. :-k

---

### Post by Maju on 2010-03-02
> **El Zoido said:**
> Would still be interesting to find out what exactly is happening every night at that time. :-k

I'm guessing that if the issue is some virus in some other computer other than my own (as has been suggested here), I can imagine it's the pre-scheduled time it has to scan ports/send spam or whatever. However as the "candidate" PC is not around/active, as the owner has been outside for a whole month already, I can't make any check.

Another maybe simpler possibility might be that it is the exact time when the server's computers are switched between unit A and unit B. I used to be a manteinance worker in one of such network servers in the proto-Internet age (i.e. the earliest 90s) and every night at certain hour we had to operate that switch with due care, which might (then) interrupt service for a matter of seconds (it was like 15 mins interruption in the oldest server we had, which was only used by a few teletypes anymore). Nowadays maybe that procedure is automated (hence the exact time) and the interruption of service may be totally imperceptible. 

Imperceptible... except for the modem, which would then send a USB signal switching some issue (bug) related to either my AMD Athlon 64 or the Intrepid Ibex upgrade or the interaction between both (because as I said before, it never happened with Hardy: only since I upgraded to Intrepid).

That's my best guess. 1:00 am local time looks like a nice "safe" scheduled time to make the daily switch between the twin servers. If something goes wrong and service is cut temporarily, most customers will be sleeping (as was I).

---

### Post by El Zoido on 2010-03-02
Although I would find it strange if it had to do with the OS.
If you shut your pc down the OS should not be acitve, so it's probably caused by the mainboard and only by chance did it coincide with your upgrade.
Anyway an interesting story... ;)

---

