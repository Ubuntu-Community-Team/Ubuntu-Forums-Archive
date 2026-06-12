---
title: "new partition"
date: 2006-05-21
forum: General Help
---

### Post by shredfitz on 2006-05-21
My ubuntu 5.10 is installed on a 40 gb drive and my xp is installed on a 160 gb hard drive.  I just partitioned my 160 gb so that I now have a new partition of 100 gb formatted ext 3 .  I want to start storing files that I acquire while running ubuntu in that new partition but I cannot figure out how to get that lock icon off of the folder that represents my new partition.  I have followed the how - tos but I still just dont get it.  I might be an idiot and I am sure that it is a simple step.  How exactly do I do this ?  THank you.

---

### Post by aysiu on 2006-05-21
Which HowTo did you follow?

First, figure out the location of your new partition. ```
sudo fdisk -l
``` should give you a list.

Let's assume for this example, that it's /dev/hda5. ```
sudo umount /dev/hda5
sudo mkdir /data
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` Add on this line ```
/dev/hda5 /data ext3 defaults 0 0
``` Save and exit ```
sudo mount -a
sudo chown -R shredfitz:shredfitz /data
sudo chmod -R 755 /data
```

---

### Post by shredfitz on 2006-05-21
okay won't work.  This is what happened :



brian@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6708    53881978+   7  HPFS/NTFS
/dev/hda2            6709       19457   102406342+   f  W95 Ext'd (LBA)
/dev/hda5            6709       19457   102406311   83  Linux

Disk /dev/hdd: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4806    38604163+  83  Linux
/dev/hdd2            4807        4982     1413720    f  W95 Ext'd (LBA)
/dev/hdd5            4807        4982     1413688+  82  Linux swap / Solaris

Disk /dev/sda: 15 MB, 15990784 bytes
4 heads, 32 sectors/track, 244 cylinders
Units = cylinders of 128 * 512 = 65536 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243       15536    1  FAT12
brian@ubuntu:~$ sudo umount /dev/hda5
umount: /dev/hda5: not mounted
brian@ubuntu:~$ sudo mkdir /data
mkdir: cannot create directory `/data': File exists
brian@ubuntu:~$ sudo cp /etc/fstab /etc/fstab_backup
brian@ubuntu:~$ gksudo gedit /etc/fstab

(gedit:9721): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by aysiu on 2006-05-21
[QUOTE=shredfitz]```
brian@ubuntu:~$ gksudo gedit /etc/fstab

(gedit:9721): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```[/QUOTE] That warning comes up when you launch *gksudo gedit* from the terminal, but it still works, and Gedit should be launched. Just go ahead and use it. > ```
brian@ubuntu:~$ sudo mkdir /data
mkdir: cannot create directory `/data': File exists
``` You already have a folder called /data?

---

### Post by jones_jj on 2006-05-21
shredfitz, I need to know a few things.  First when you say there is a lock icon on the directory, who is the owner of the directory?  When you created the new partition did you give it a name, e.g. something like /data, /files, etc?  What did you use to partition the new 100GBs?  Did you use Partition Magic, Ubuntu disk manager, etc?

---

### Post by shredfitz on 2006-05-21
[QUOTE=jones_jj]shredfitz, I need to know a few things.  First when you say there is a lock icon on the directory, who is the owner of the directory?  When you created the new partition did you give it a name, e.g. something like /data, /files, etc?  What did you use to partition the new 100GBs?  Did you use Partition Magic, Ubuntu disk manager, etc?[/QUOTE]


I used gparted.  I figured it out .  Thanks.  I am sure I will need more help with this in the near future.  When I reboot sometime soon,  will I need to mount the drive again ? 

The way I did it this time was through System->Admin->Disks.  I enabled the partition and set the access path as : /second_drive.

I then mounted it in the terminal.

I guess I did it right.

---

### Post by jones_jj on 2006-05-22
You will need to mount it each time, unless it's in your /etc/fstab file.  Was there an option with System->Admin->Disks to auto mount the directory?

If not, take a look at your /etc/fstab file and then follow what's already there, and add the new partition to the file.  Reboot and all should be good to go.

---

### Post by shredfitz on 2006-05-22
thanks to everybody.

---

