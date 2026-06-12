---
title: "USB drive mounts as a cdrom"
date: 2010-02-12
forum: General Help
---

### Post by narnie on 2010-02-12
Hello,

I have a curious problem.

I have a USB drive that is mounting as a cdrom on /dev/sr1 instead of a /dev/sdX where X is usually a "b" if no other usb drives are present.

I can't erase the filesystem because it is listed as read only.

```

$ mount|grep /dev/sr1
/dev/sr1 on /media/AUTORUN type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)

```

```
$ cat /etc/fstab 
proc            /proc           proc    defaults        0       0
UUID=022a5a8e-c4b4-4117-9301-71cbbfcab264 /               ext3    errors=remount-ro 0       1
UUID=47deb42a-b371-4656-9000-cdc8002272ea /home           ext3    defaults        0       2
UUID=cf25e4c0-975d-4ae3-b0bd-5ef8bd0ddcc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc4608ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12641   100000000    7  HPFS/NTFS
/dev/sda3           59465       60802    10739712   17  Hidden HPFS/NTFS
/dev/sda4           12641       59464   376105748    5  Extended
/dev/sda5           12642       19168    52428127+  83  Linux
/dev/sda6           19169       58942   319484623+  83  Linux
/dev/sda7           58943       59464     4192933+  82  Linux swap / Solaris

```

I remember reading something a year ago about a problem with a broadband wireless card having a similar problem as it had 2 filesystems on there. Under Windows, the first one installs an when unmounted, the second is visible. I think the fix involved something with udev, but it is beyond me how this was done. I'm thinking this may be a similar problem.

Any ideas on how to get this to mount correctly? I'm interested in wiping the thing and using it if poss.

With thanks,
Narnie

---

### Post by narnie on 2010-02-12
Tried this but as one can see, it didn't work.

```

$ sudo mount -o rw /dev/sr1 /media/ntfs
mount: block device /dev/sr1 is write-protected, mounting read-only

```

---

### Post by narnie on 2010-02-12
Also, I should have included this:

from /var/log/messages:

```

Feb 12 01:33:46 toshiba-laptop kernel: [ 3102.241322] usb 6-2: new full speed USB device using uhci_hcd and address 4
Feb 12 01:33:46 toshiba-laptop kernel: [ 3102.413386] usb 6-2: configuration #1 chosen from 1 choice
Feb 12 01:33:46 toshiba-laptop kernel: [ 3102.415479] scsi8 : SCSI emulation for USB Mass Storage devices
Feb 12 01:33:51 toshiba-laptop kernel: [ 3107.414214] scsi 8:0:0:0: CD-ROM                                      1.00 PQ: 0 ANSI: 2
Feb 12 01:33:51 toshiba-laptop kernel: [ 3107.421353] sr1: scsi3-mmc drive: 0x/0x caddy
Feb 12 01:33:51 toshiba-laptop kernel: [ 3107.421767] sr 8:0:0:0: Attached scsi generic sg2 type 5
Feb 12 01:33:51 toshiba-laptop kernel: [ 3107.431224] sr1: Hmm, seems the drive doesn't support multisession CD's

```

and also this
```

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 1130:9801 Tenx Technology, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d104 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The Tenx Technology is the "offending" device

---

### Post by rnerwein on 2010-02-12
hi narnie
i can't help you - but you are not alone. have a look at my configuration.
lsusb gives me.
[COLOR=DarkRed]Bus 002 Device 005: ID 057c:8402 AVM GmbH [/COLOR]
[COLOR=Red]Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device[/COLOR]
Bus 002 Device 003: ID 0951:1613 Kingston Technology 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 152e:1640 LG (HLDS) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and: /etc/udev/rules.d/70-persistent-cd.rules
#[COLOR=Blue] WLAN_selfinstall (pci-0000:00:02.1-usb-0:2:1.0-scsi-0:0:0:0)[/COLOR]
SUBSYSTEM=="block", ENV{[COLOR=Red]ID_CDROM[/COLOR]}=="?*", [COLOR=Blue]ENV{ID_SERIAL}=="FRITZ__WLAN_selfinstall_001F3F08FCAE-0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"[/COLOR]

if no problem with that "WRONG" configuration. every thing works ok (ha i don't) try to realy want to write to my wlan stick !
but more searius is that: [COLOR=Red]Realtek Semiconductor Corp. Mass Stroage Device
[COLOR=Black]my box have never seen a Realtek Mass Storage Device - and for sure it's not present ! must be hard code in the kernel or any where ???.
you see - you are not alone.
ciao
[/COLOR][/COLOR]

---

### Post by dcstar on 2010-02-12
> **narnie said:**
> Hello,

I have a curious problem.

I have a USB drive that is mounting as a cdrom on /dev/sr1 instead of a /dev/sdX where X is usually a "b" if no other usb drives are present.

I can't erase the filesystem because it is listed as read only.
........

It is possible that the data on the device is a CD-ROM image file.

You should be able to see it in the partition manager and unmount and format it as normal.

---

### Post by narnie on 2010-02-12
> **dcstar said:**
> It is possible that the data on the device is a CD-ROM image file.

You should be able to see it in the partition manager and unmount and format it as normal.

Unfortunately, neither parted nor gparted see the mounted usb because of the way it mounts :(

---

### Post by KittyChunk on 2011-01-15
Hi narnie, did you ever have any success with this?

I'm having similar problems with a Verbatim V-Secure Executive USB drive in Ubuntu. This drive has a separate small partition containing some (Windows-only, sigh) login and encryption software, which is all that mounts when the drive is plugged into an Ubuntu machine. On a Windows box, the software then autoruns, asks you for a password, and then mounts the rest of the drive space as a separate partition.

In Ubuntu, fdisk/gparted etc don't even see the small partition after the drive has mounted (it only mounts read-only on /dev/sr1, just like your prob above), so no dice reformatting it from linux. In Windows, the partition structure on the drive is also locked even after you've logged in with the password, so Windows' built-in tools aren't able to delete or reformat the partitions either

This drive was given to me as a gift, but it's basically a doorstop unless I can find a way to reformat it for normal use in Ubuntu... any suggestions? I have other flash drives so don't really care if I hose it at this point :), just curious to see if I can get it working.

-q

---

