---
title: "USB thumb drive fails to automount"
date: 2006-03-17
forum: General Help
---

### Post by h3llfyr3 on 2006-03-17
Heya, frist post ;)
Having an issue with my a USB thumb drive, not automounting. 
I ended up removing it (unmount 'ed first then removed it) swapped another one in and it would'nt automount. I tried mount -t vfat /dev/sda /mnt/usb (i mounted to /mnt instead of /media) and it won't mount. 

Mount's fine on my 'other Ubuntu' box so it is not the filesystem as the message suggests,  ....any thoughts?
 
root@Ares:~# mount -t vfat /dev/sda /mnt/usb/
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 3
[4295364.307000] SCSI error : <0 0 0 0> return code = 0x6000000
[4295364.307000] end_request: I/O error, dev sda, sector 0
[4295364.307000] Buffer I/O error on device sda, logical block 0
[4295364.307000]  unable to read partition table
[4295364.307000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4295364.323000] FAT: invalid media value (0x01)
[4295364.323000] VFS: Can't find a valid FAT filesystem on dev sda.
[4295365.049000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).

---

### Post by Sutekh on 2006-03-18
[QUOTE=h3llfyr3]
...
mount: **wrong fs type**, bad option, bad superblock on /dev/sda,
... 
 
...
[4295364.323000] VFS: **Can't find a valid FAT filesystem on dev sda**.
...
[/QUOTE]
Seems to me that the USB drive is not formatted FAT, or there is an error with the formatting.  Can you verify the formatting of the USB drive?

What is the output of this code (when the USB plugged in)
```
sudo fdisk -l
```

---

### Post by h3llfyr3 on 2006-03-18
The same drive works no problem when plugged into my laptop (also running ubuntu same version). So the filesystem is not an issue.

Many thanks for the response.

---

### Post by powder on 2006-03-18
Are you sure you're using /dev/sda and not perhaps /dev/sda1?

---

### Post by h3llfyr3 on 2006-03-19
With the USB device plugged in:

root@Ares:~# fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        4868    23744070   83  Linux
/dev/hda3            4869        4998     1044225    5  Extended
/dev/hda5            4869        4998     1044193+  82  Linux swap / Solaris

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/hdb2            3825       30515   214394040    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

However another USB stick does work when plugged in and this non-working usb stick works in my ubuntu laptop...

root@Ares:~# ls /dev |grep sda*
ptysd
sda
ttysd
root@Ares:~# cat /var/log/syslog |tail

Mar 19 09:13:33 localhost kernel: [4298093.897000] usb 2-1: reset full speed USB device using ohci_hcd and address 3
Mar 19 09:13:53 localhost kernel: [4298114.011000] SCSI error : <0 0 0 0> return code = 0x70000
Mar 19 09:13:53 localhost kernel: [4298114.011000] end_request: I/O error, dev sda, sector 0
Mar 19 09:13:53 localhost kernel: [4298114.011000] Buffer I/O error on device sda, logical block 0
Mar 19 09:15:33 localhost kernel: [4298214.085000] usb 2-1: reset full speed USB device using ohci_hcd and address 3

---

### Post by Pragmatist on 2006-03-22
Here is what you want:
[http://nst.sourceforge.net/nst/docs/user/ch04s04.html](http://nst.sourceforge.net/nst/docs/user/ch04s04.html)

The key is to create a filesystem on the drive.

---

### Post by tebibyte on 2006-03-27
The same thing happened to me. My floppy drive isn't working at all, either. It worked before, but now I don't know the problem is. I'm a newbie when it comes to linux. I could really use some help. Thank you.

P.S. I would like it to work Automaticly, like it should, without having to go through the trouble of making a virtual ext3 filesystem for each media I put in. That is way over my head.

---

