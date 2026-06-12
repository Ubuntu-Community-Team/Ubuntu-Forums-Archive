---
title: "Mounting ntfs fails!"
date: 2006-03-10
forum: General Help
---

### Post by cnich23 on 2006-03-10
I have two harddrives in my system. Primary drive is Sata and has 2 partions one of which is windows and the other ubuntu.  My second drive is an IDE and only has 1 ntfs partition.

Now ubuntu sees the ide disk but I simply can't mount it. 

I countinue to receive /dev/hda is already mounted  when it is not mounted

any suggestions would be much appreciated

---

### Post by Zelut on 2006-03-10
I'm just taking a guess here but it sounds like if you have two drives, and ubuntu is on the first, that the SATA drive would be /dev/hda and your second IDE drive would be something like /dev/hdb ?  You might want to try:

sudo fdisk -l (I believe) to list disks on the machine.  Perhaps you're just not mounting it quite right.  /dev/hdb1, etc mght work..

---

### Post by cnich23 on 2006-03-10
no my sata shows up as 
/dev/sda

and in the System->Administration->Disks
the IDE shows up as /dev/hda

---

### Post by Zelut on 2006-03-10
When I mount my NTFS partition I need to use /dev/hda1.  Are you using that or just /dev/hda?

This is the line from my /etc/fstab for mounting my NTFS partition:
/dev/hda1       /media/XP       ntfs    nls=utf8,umask=0222 0     0

---

### Post by aysiu on 2006-03-10
kuyaedz is on the right track.

For more details:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

For even more details:
[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)

---

### Post by cnich23 on 2006-03-10
No I have also already tried this and this also fails, I receive special media does not exist

---

### Post by aysiu on 2006-03-10
[QUOTE=cnich23]No I have also already tried this and this also fails, I receive special media does not exist[/QUOTE] Can you go to Applications > Accessories > Terminal and then post here the output of these three separate commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by cnich23 on 2006-03-10
Disk /dev/hda: 163.9 GB, 163928604672 bytes
16 heads, 63 sectors/track, 317632 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1      317629   160084984+   7  HPFS/NTFS

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7397    59416371    7  HPFS/NTFS
/dev/sda2            7398        9900    20105347+  83  Linux
/dev/sda3            9901       10011      891607+   5  Extended
/dev/sda5            9901       10011      891576   82  Linux swap / Solaris

=========================================

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  1.8G   17G  10% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/hdc              7.9G  7.9G     0 100% /media/cdrom0

==========================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aysiu on 2006-03-10
Follow these steps exactly (copy and paste if you don't trust your typing skills):

```
sudo umount /dev/hda1
sudo umount /dev/sda1
sudo mkdir /windows_1
sudo mkdir /windows_2
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace your entire /etc/fstab with this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /windows_1 ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /windows_2 ntfs nls=utf8,umask=0222 0 0
``` Save it and exit Gedit. Then ```
sudo mount -a
```

---

### Post by cnich23 on 2006-03-10
it is wierd to whole problem seems liek the ide drive just doesnt exist but its seen


when i try to umount it 
umount: /dev/hda1: not found

and even trying to automount on startup fails with fstab

---

### Post by aysiu on 2006-03-10
I hate to say it, but maybe your drive is... damaged.

---

### Post by cnich23 on 2006-03-10
I couldn't imagine why I hav ebeen using it for 3 months now and it still works perfectly in windows

This is the message i receive when I attempt the mount
mount: special device /dev/hda1 does not exist

---

