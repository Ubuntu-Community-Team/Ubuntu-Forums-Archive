---
title: "Integrated Card Reader doesn't work and causes mouse to hang at startup"
date: 2010-11-24
forum: General Help
---

### Post by biggerben on 2010-11-24
Everything worked fine in Kubuntu 10.04 (64-bit). On the upgrade to 10.10 (64-bit) it takes about a minute until I can move the mouse after startup and the integrated memory card reader doesn't work (but the green LED which used to only come on when there was a card in there is now always on).

This has been discussed twice before:
[here]("http://ubuntuforums.org/showthread.php?t=1595203&highlight=device+-accepting+address+error+-110") (closed and solved by unplugging cardreader which I do not want to do)
[and here]("http://ubuntuforums.org/showthread.php?t=1579693") (unsolved but closed as maverick no longer in beta)

dmesg (note the errer -110) follows. Let me know if I can/should include any other logs/info!

Many thanks to any attempts to solve this, whether successful or not :)

```

[   13.575002] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   13.790470] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.903728] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   16.280020] usb 1-5: device descriptor read/64, error -110
[   17.375755] sky2 0000:02:00.0: eth0: enabling interface
[   17.376174] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.377028] type=1400 audit(1290608578.996:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=897 comm="apparmor_parser"
[   17.377066] type=1400 audit(1290608578.996:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=898 comm="apparmor_parser"
[   17.377816] skge 0000:05:02.0: eth1: enabling interface
[   17.378922] type=1400 audit(1290608578.996:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=895 comm="apparmor_parser"
[   17.379455] type=1400 audit(1290608578.996:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=895 comm="apparmor_parser"
[   17.379752] type=1400 audit(1290608578.996:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=895 comm="apparmor_parser"
[   17.381192] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.381803] type=1400 audit(1290608579.006:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=896 comm="apparmor_parser"
[   17.382451] type=1400 audit(1290608579.006:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=896 comm="apparmor_parser"
[   17.415201] ppdev: user-space parallel port driver
[   19.082575] skge 0000:05:02.0: eth1: Link is up at 100 Mbps, full duplex, flow control both
[   19.083026] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   19.738149] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   19.758735] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   19.761153] EXT4-fs (sda4): re-mounted. Opts: commit=0
[   27.941862] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   27.944057] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   28.111149] EXT4-fs (sda4): re-mounted. Opts: commit=0
[   29.491259] eth1: no IPv6 routers present
[   31.521268] usb 1-5: device descriptor read/64, error -110
[   31.751269] usb 1-5: new high speed USB device using ehci_hcd and address 3
[   46.870018] usb 1-5: device descriptor read/64, error -110
[   51.677245] lo: Disabled Privacy Extensions
[   62.091075] usb 1-5: device descriptor read/64, error -110
[   62.320018] usb 1-5: new high speed USB device using ehci_hcd and address 4
[   72.741261] usb 1-5: device not accepting address 4, error -110
[   72.861262] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   83.281261] usb 1-5: device not accepting address 5, error -110
[   83.281275] hub 1-0:1.0: unable to enumerate USB device on port 5
[   83.620021] usb 2-4: new high speed USB device using ehci_hcd and address 4
[   83.829254] Initializing USB Mass Storage driver...
[   83.829376] scsi6 : usb-storage 2-4:1.0
[   83.829851] usbcore: registered new interface driver usb-storage
[   83.829853] USB Mass Storage support registered.
[   84.180014] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   84.865209] scsi 6:0:0:0: Direct-Access     ST364032 3AS                   PQ: 0 ANSI: 2 CCS
[   84.865681] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   84.866202] sd 6:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[   84.866704] sd 6:0:0:0: [sdc] Write Protect is off
[   84.866708] sd 6:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   84.866710] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   84.868178] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   84.868210]  sdc: sdc1 sdc2
[   84.874709] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   84.874714] sd 6:0:0:0: [sdc] Attached SCSI disk
[   99.301294] usb 5-1: device descriptor read/64, error -110
[  114.530015] usb 5-1: device descriptor read/64, error -110
[  114.760015] usb 5-1: new full speed USB device using uhci_hcd and address 3
[  129.881266] usb 5-1: device descriptor read/64, error -110
[  145.110019] usb 5-1: device descriptor read/64, error -110
[  145.340021] usb 5-1: new full speed USB device using uhci_hcd and address 4
[  155.761262] usb 5-1: device not accepting address 4, error -110
[  155.890021] usb 5-1: new full speed USB device using uhci_hcd and address 5
[  166.301267] usb 5-1: device not accepting address 5, error -110
[  166.301286] hub 5-0:1.0: unable to enumerate USB device on port 1
[  166.581279] usb 6-1: new low speed USB device using uhci_hcd and address 2
[  166.800499] usbcore: registered new interface driver hiddev
[  166.814785] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3
[  166.814911] generic-usb 0003:046D:C043.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[  166.814935] usbcore: registered new interface driver usbhid
[  166.814937] usbhid: USB HID core driver
[  167.052520] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  167.215667] hub 7-1:1.0: USB hub found
[  167.217638] hub 7-1:1.0: 4 ports detected
[  167.502527] usb 8-1: new full speed USB device using uhci_hcd and address 2
[  167.739984] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1204
[  167.740008] usbcore: registered new interface driver usblp
[  168.880355] usb 8-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  817.658835] EXT4-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
[  817.665448] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[  823.017767] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[  879.020018] usb 1-2: new high speed USB device using ehci_hcd and address 6
[  879.760018] usb 5-1: new full speed USB device using uhci_hcd and address 6
[  894.881275] usb 5-1: device descriptor read/64, error -110
[  910.111263] usb 5-1: device descriptor read/64, error -110
[  910.346148] usb 5-1: new full speed USB device using uhci_hcd and address 7
[  925.470018] usb 5-1: device descriptor read/64, error -110
[  940.701263] usb 5-1: device descriptor read/64, error -110
[  940.931272] usb 5-1: new full speed USB device using uhci_hcd and address 8
[  951.350012] usb 5-1: device not accepting address 8, error -110
[  951.483675] usb 5-1: new full speed USB device using uhci_hcd and address 9
[  961.901264] usb 5-1: device not accepting address 9, error -110
[  961.901287] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 1550.080015] usb 5-1: new full speed USB device using uhci_hcd and address 10
[ 1565.210249] usb 5-1: device descriptor read/64, error -110
[ 1580.441263] usb 5-1: device descriptor read/64, error -110
[ 1580.670013] usb 5-1: new full speed USB device using uhci_hcd and address 11
[ 1595.790022] usb 5-1: device descriptor read/64, error -110
[ 1611.030016] usb 5-1: device descriptor read/64, error -110
[ 1611.260013] usb 5-1: new full speed USB device using uhci_hcd and address 12
[ 1621.691259] usb 5-1: device not accepting address 12, error -110
[ 1621.803092] usb 5-1: new full speed USB device using uhci_hcd and address 13
[ 1632.221259] usb 5-1: device not accepting address 13, error -110
[ 1632.221273] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 1632.221295] usb 1-2: USB disconnect, address 6
[ 1632.501268] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 2603.117213] usb 1-2: USB disconnect, address 7
[ 4773.905898] lo: Disabled Privacy Extensions
[ 4893.413558] lo: Disabled Privacy Extensions
[ 5778.475489] lo: Disabled Privacy Extensions
[ 5841.996874] lo: Disabled Privacy Extensions
[ 7830.100762] lo: Disabled Privacy Extensions
[15321.464716] lo: Disabled Privacy Extensions
[16718.005207] lo: Disabled Privacy Extensions
[16770.760016] usb 2-2: new high speed USB device using ehci_hcd and address 6
[16770.928246] scsi7 : usb-storage 2-2:1.0
[16771.926863] scsi 7:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[16771.927344] sd 7:0:0:0: Attached scsi generic sg4 type 0
[16771.936850] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[18188.252913] lo: Disabled Privacy Extensions

```

---

### Post by biggerben on 2010-11-25
should I add my entire dmesg or anything else for that matter?

---

### Post by biggerben on 2010-11-27
hmm, or should I just file a bug at launchpad?

---

