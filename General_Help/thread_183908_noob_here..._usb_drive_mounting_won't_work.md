---
title: "noob here... usb drive mounting won't work"
date: 2006-05-28
forum: General Help
---

### Post by ianseballe on 2006-05-28
help! i get this message:

Error: given UDI is not a mountable volume

but my usb drive works in xp...

](*,) :(

---

### Post by Sutekh on 2006-05-28
What format is the USB?

Try reading and following this link

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

OR post the output from this command, which lists the partitions available
```
sudo fdisk -l
```
and this command, which lists the contents of your mounting configuration file
```
cat /etc/fstab
```

---

### Post by Andrew1234 on 2006-05-29
I have the same issue ,is it possible to have a usb memory stick to use in Ubuntu and Xp so I can transfer files from one operating system to the other?

---

### Post by Sutekh on 2006-05-29
[quote=Andrew1234]I have the same issue ,is it possible to have a usb memory stick to use in Ubuntu and Xp so I can transfer files from one operating system to the other?[/quote]Of course its perfectly possible.

Its just a little harder with Windows-type partitions.

Try the link in my original post, its very clear on what needs to be done.

If you are still stuck, open a Terminal (Applications -> Accessories Menu) and use those commands to provide the neccessary information, and we can work it out for you, and step you through it.

---

### Post by Andrew1234 on 2006-05-30
Thank you Sukekh I have had a loojk at this page and given it a try with out sucess below is my information:-
Disk /dev/hda: 10.1 GB, 10141286400 bytes
255 heads, 63 sectors/track, 1232 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1178     9462253+  83  Linux
/dev/hda2            1179        1232      433755    5  Extended
/dev/hda5            1179        1232      433723+  82  Linux swap / Solaris

Disk /dev/hdc: 1083 MB, 1083801600 bytes
64 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         525     1058368+   6  FAT16

Disk /dev/sda: 254 MB, 254279680 bytes
64 heads, 32 sectors/track, 242 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1         243      248304    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 63, 32) logical=(242, 31, 32)



  GNU nano 1.3.8             File: /etc/fstab



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0


I see /dev/sda1   ?           1         243      248304    4  FAT16 <32M being the disk I am wanting.

Many thanks

---

### Post by Andrew1234 on 2006-06-03
I have tried several different ways to get the USB memory stick to work but still I cannot get any results, updated details:-

My fstab setting which I have altered:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/windows  vfat    iocharset=utf8,umask=000   0       0

When I try to mount the drive I get this error:-

andrew@shopmail:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If I try to open the memory stick(Flash Drive SM 2.0)in File browser I get this error:-

mount: only root can mount /dev/sda on /media/windows

Any help please!

Just plugged in another brand of memory stick and this one works fine any ideas why?

---

### Post by Sutekh on 2006-06-03
[quote=Andrew1234]
/dev/sda        /media/windows  vfat    iocharset=utf8,umask=000   0       0
[/quote]
If you use ```
/dev/sda**1**        /media/windows  vfat    **user,**iocharset=utf8,umask=000   0       0
```
Then it should work and ordinary users should be able to mount.

What concerns me was the fdisk output...
[quote=Andrew1234] Disk /dev/sda: 254 MB, 254279680 bytes
64 heads, 32 sectors/track, 242 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
[B]
This doesn't look like a partition table
Probably you selected the wrong device.[/B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1         243      248304    4  FAT16 <32M
** Partition 1 has different physical/logical endings:**
**      phys=(249, 63, 32) logical=(242, 31, 32)**
[/quote]
I'm not 100% on how you can fix this

---

