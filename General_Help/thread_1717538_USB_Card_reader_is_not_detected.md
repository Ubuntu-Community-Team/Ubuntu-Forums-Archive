---
title: "USB Card reader is not detected"
date: 2011-03-30
forum: General Help
---

### Post by Siva Sankaran on 2011-03-30
I have installed Ubuntu 10.10 in my system. I have plug in th USB card reader but it is not detected. Eventhough the same card is detected when I'd pluged in at last  night and I have just browse the folders in the memory card.
Then I just right click on the icon in media folder and click eject

the texts in file[SIZE=3] /var/log/messages  [/SIZE]for above operation 


```

Mar 29 20:59:07 workstation kernel: [14963.412719] scsi 7:0:0:0: Direct-Access     FNK TECH  USB CARD READER 2.33 PQ: 0 ANSI: 2
Mar 29 20:59:07 workstation kernel: [14963.413425] sd 7:0:0:0: Attached scsi generic sg2 type 0
Mar 29 20:59:07 workstation kernel: [14963.414646] sd 7:0:0:0: [sdb] 990976 512-byte logical blocks: (507 MB/483 MiB)
Mar 29 20:59:07 workstation kernel: [14963.416840] sd 7:0:0:0: [sdb] Write Protect is off
Mar 29 20:59:07 workstation kernel: [14963.420067]  sdb:
Mar 29 20:59:07 workstation kernel: [14963.422313] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Mar 29 20:59:18 workstation kernel: [14974.092035] usb 1-2: reset high speed USB device using ehci_hcd and address 6
Mar 29 20:59:22 workstation kernel: [14978.092065] usb 1-2: USB disconnect, address 6
Mar 29 20:59:22 workstation kernel: [14978.094200] VFS: busy inodes on changed media or resized disk sdb
Mar 29 20:59:22 workstation kernel: [14978.094288] VFS: busy inodes on changed media or resized disk sdb
Mar 29 20:59:22 workstation kernel: [14978.099718] VFS: busy inodes on changed media or resized disk sdb
Mar 29 20:59:22 workstation kernel: [14978.102981] VFS: busy inodes on changed media or resized disk sdb
Mar 29 21:00:52 workstation kernel: [15068.248529] usb 1-2: new high speed USB device using ehci_hcd and address 7
Mar 29 21:00:52 workstation kernel: [15068.381421] scsi8 : usb-storage 1-2:1.0
Mar 29 21:00:53 workstation kernel: [15069.381150] scsi 8:0:0:0: Direct-Access     FNK TECH  USB CARD READER 2.33 PQ: 0 ANSI: 2
Mar 29 21:00:53 workstation kernel: [15069.381867] sd 8:0:0:0: Attached scsi generic sg2 type 0
Mar 29 21:00:53 workstation kernel: [15069.382874] sd 8:0:0:0: [sdb] 990976 512-byte logical blocks: (507 MB/483 MiB)
Mar 29 21:00:53 workstation kernel: [15069.384629] sd 8:0:0:0: [sdb] Write Protect is off
Mar 29 21:00:53 workstation kernel: [15069.387321]  sdb:
Mar 29 21:00:53 workstation kernel: [15069.391129] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Mar 29 21:01:41 workstation kernel: [15117.224399] usb 1-2: USB disconnect, address 7
Mar 29 21:02:40 workstation kernel: [15176.250224] lo: Disabled Privacy Extensions

``` When I plug in the USB Card reader there is no change in last part of the log file

It is same as follows:

```

Mar 30 10:39:39 workstation kernel: [   12.707887] r8169 0000:03:00.0: eth0: link up
Mar 30 10:39:39 workstation kernel: [   12.712591] type=1400 audit(1301461779.747:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=962 comm="apparmor_parser"
Mar 30 10:39:39 workstation kernel: [   12.712794] type=1400 audit(1301461779.747:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=963 comm="apparmor_parser"
Mar 30 10:39:39 workstation kernel: [   12.713336] type=1400 audit(1301461779.747:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=963 comm="apparmor_parser"
Mar 30 10:39:39 workstation kernel: [   12.713632] type=1400 audit(1301461779.747:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=963 comm="apparmor_parser"
Mar 30 10:39:39 workstation kernel: [   12.721072] type=1400 audit(1301461779.755:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=970 comm="apparmor_parser"
Mar 30 10:39:39 workstation kernel: [   12.721871] type=1400 audit(1301461779.755:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=970 comm="apparmor_parser"
Mar 30 10:39:39 workstation kernel: [   12.726879] type=1400 audit(1301461779.759:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=965 comm="apparmor_parser"
Mar 30 10:39:40 workstation kernel: [   13.753604] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Mar 30 10:39:41 workstation kernel: [   14.924086] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Mar 30 10:39:50 workstation kernel: [   23.014398] padlock: VIA PadLock not detected.
Mar 30 10:40:59 workstation kernel: [   92.632295] lo: Disabled Privacy Extensions

```And also usb card reader is not listed in output of the command [SIZE=3]sudo fdisk -l

[SIZE=1]the output is

[/SIZE][/SIZE]```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x022c022b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60800   437176814+   f  W95 Ext'd (LBA)
/dev/sda5            6375       21672   122881153+  83  Linux
/dev/sda6           21803       40794   152547328    7  HPFS/NTFS
/dev/sda7           40795       60800   160698163+   7  HPFS/NTFS
/dev/sda8           21673       21802     1043456    7  HPFS/NTFS

Partition table entries are not in disk order


```[SIZE=3]

[/SIZE]I don't know device name to manually mount the USB card reader[SIZE=3]
[/SIZE]
Please tell me how to get rid of this problem

---

### Post by tanics on 2011-08-15
I have a cheap usb card reader "FNK TECH" - though I can see the icon of it appears in Places > Computer or in System > Administration > Disk utility but can't mount the SD card or can't do anything.
Trying to format it from "Disk utility"  but gives an error message - "cannot open /dev/sdb: No medium found". 
What's the problem - is there any solution?

Thanks

---

### Post by slant53 on 2011-08-24
I have Ubuntu 11.04 installed and also cannot get my SDHC cards in my USB card reader reader detected.  When I insert a card, the following shows up dmesg
[ 2545.818376] usb 2-3.3.2: USB disconnect, address 19
[ 2545.818487] sd 13:0:0:3: [sdk] READ CAPACITY failed
[ 2545.818494] sd 13:0:0:3: [sdk]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK

Disk Utility shows the slots in the reader but they all report no media present (including the slot with the card in it)

lsusb also detects the reader:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c069 Logitech, Inc. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 413c:5516 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 10df:0500 In-Win Development, Inc. iAPP CR-e500 Card reader
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 04b8:0130 Seiko Epson Corp. Perfection V500 (GT-X770)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

but fdisk -l does not see anything

---

