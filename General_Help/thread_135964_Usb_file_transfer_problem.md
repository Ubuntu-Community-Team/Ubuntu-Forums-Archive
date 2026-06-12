---
title: "Usb file transfer problem"
date: 2006-02-24
forum: General Help
---

### Post by projecteternity on 2006-02-24
I'm new to ubuntu and recently I tried to get my usb thumbdrive to work.

I plugged it in and the computer appeared to recognize it but when I went to add files they would disappear when I removed the drive and plug it back in again.

I have also had a similar problem transferring to my nokia 770 where all the files I send appear to be 0 bytes on the device.

---

### Post by aysiu on 2006-02-25
Can you plug the USB drive into your computer and then post in this thread the output of the following three *separate* commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by projecteternity on 2006-02-25
Ok, here is what I got:

benoit@Erasmus:~$ sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        4862    39013852+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       15633   125572041    7  HPFS/NTFS
/dev/hdb2           15634       18247    20996955   83  Linux
/dev/hdb3           18248       18855     4883760    5  Extended
/dev/hdb5           18248       18855     4883728+  82  Linux swap / Solaris

Disk /dev/sda: 131 MB, 131072000 bytes
16 heads, 32 sectors/track, 500 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         499      127728    6  FAT16


benoit@Erasmus:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2              20G  4.3G   15G  23% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda1              40M  7.1M   33M  19% /media/hda1
/dev/hda2              38G   27G   11G  73% /media/hda2
/dev/hdb1             120G   42G   79G  35% /media/hdb1
/dev/sda1             125M  5.2M  120M   5% /media/usbdisk

benoit@Erasmus:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2006-02-25
Okay. That's weird. Theoretically, it should automount with the correct permissions, but we may just have to fix that in the /etc/fstab. ```
sudo umount /dev/sda1
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace your **entire** /etc/fstab with this ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 vfat defaults 0 0
/dev/hda2 /media/hda2 ntfs defaults 0 0
/dev/hdb1 /media/hdb1 ntfs defaults 0 0
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Save the file and exit Gedit. Finally ```
sudo mount -a
``` Any difference?

---

### Post by projecteternity on 2006-02-25
I'm still having the same problem only it doesn't automount anymore.

---

### Post by aysiu on 2006-02-25
[QUOTE=projecteternity]I'm still having the same problem only it doesn't automount anymore.[/QUOTE] Yikes! Take that line out of the /etc/fstab then. Sorry! I'm not sure what the problem is.

---

### Post by projecteternity on 2006-02-25
As a test I loaded up a knoppix live cd and it wasn't even able to find the drive, but it found the nokia 770 and rather than writing blank files it just said unable to write to disk.

Although everything works fine under windows.

---

