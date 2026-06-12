---
title: "Problem to mount samsung soul phone mass storage"
date: 2009-10-17
forum: General Help
---

### Post by addadi on 2009-10-17
Hi,
I'm using Jaunty 9.04 and I'm trying to connect Samsung soul phone via usb (defined on the phone as mass storage). It always seems to fail and the phone mass straoge is not recognizable by ubuntu. I also have winxp install, unfortunatly - no problem there, the phone is identified as mass storage and automounts. so it's  not HW or bios problem.

dmesg output:
[  131.715960] usb 3-3: USB disconnect, address 3
[  136.884019] usb 3-3: new full speed USB device using ohci_hcd and address 4
[  137.099954] usb 3-3: configuration #1 chosen from 1 choice
[  137.191800] usb-storage: probe of 3-3:1.0 failed with error -5
lsusb output:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 05c6:1000 Qualcomm, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fdisk -l output:Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed853807

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       10011    65055217+   f  W95 Ext'd (LBA)
/dev/sda5            1913        7579    45520146    7  HPFS/NTFS
/dev/sda6            7580        8552     7815591   83  Linux
/dev/sda7            8553        8674      979933+  82  Linux swap / Solaris
/dev/sda8            8675       10011    10739421   83  Linux

How do I proceed from here?

Thanks,
Addadi

---

### Post by iris-n on 2009-11-12
Hi Addadi,

I hope it's not to late to help you. I had a similar problem with a samsung phone (model gt-e2120), which I have been able to solve.

1 - Comment out the line " KERNEL!="sr*", IMPORT{program}="/sbin/blkid -o udev -p $tempnode" " in the file /lib/udev/rules.d/60-persistent-storage.rules
2 - ```
ls /dev/disk/by_id/
```
3 - Plug in the phone
4 - ```
ls /dev/disk/by_id/
```
5 - See the new id that appeared (if none appeared, sorry, your problem is not this one), copy it (only the part between the hyphens).
6 - Add the line KERNEL!="sr*", ENV{ID_SERIAL}!="<paste_id_here>", IMPORT{program}="/sbin/blkid -o udev -p $tempnode" to the file in step one. <paste_id_here> is the id that you've copied. Note that it may have non-ascii characters. That is a real problem. Try to substitute them with a regular expression. If they're at the end, just delete them and put and *.Now the phone should be mannualy mountable.
7 - To enable automount, paste the following line afterwards:
KERNEL!="sr*", ENV{ID_SERIAL}=="<paste_id_here>", ENV{ID_FS_USAGE}="filesystem", ENV{ID_FS_LABEL_ENC}="my_phone"


The above solution is for karmic. For Jaunty, just replace the occurrences of IMPORT{program}="/sbin/blkid -o udev -p $tempnode" with IMPORT{program}="vol_id --export $tempnode"

I've developed this solution by using the information on [**this**]("https://bugs.launchpad.net/ubuntu/+bug/151094") bug report, which I'm planning to refile.

If the solution didn't work out for you, remember to undo the changes, otherwise your computer will not boot.

---

### Post by TenPlus1 on 2010-08-23
I tried your solution above which unfortunately did not work on my Samsung GT-E2120...  Is there anything else I can try to mount the microSD inside without having to physically take it out each time ?

---

