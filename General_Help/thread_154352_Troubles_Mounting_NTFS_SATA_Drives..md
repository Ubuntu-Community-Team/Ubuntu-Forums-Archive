---
title: "Troubles Mounting NTFS SATA Drives."
date: 2006-04-02
forum: General Help
---

### Post by oolunchbox on 2006-04-02
Ive been using Kubuntu for about 3 weeks now and I'm loving it.  Ive beenthrough a bunch of re-installs and I've finally got a lot of problems worked out (SMP kernel, nvidia drivers, twinview, usb headset with ventrilo), Ive got just one more and I'll be totally set.  When I was using windows i had 2 SATA drives that were just storage formatted NTFS.  For the life of me i cannot get them mounted in Kubuntu.  Ive gone through every how-to i can find to no avail. Somewhere I saw a command to show all the drives on the system and they showed up as /dev/sdb and /dev/sdc.  When I go into the system settings and try to mount them (I set the filesystem to NTFS, set the mount points I created [/media/d, media/g]) I get an error that the drives are in use.  In teh system settings I can see the drives with their model numbers and the such but they just dont want to mount.  I've got all my mp3s, videos, pics, etc on them and I dont want to reformat.  Does anyone have any ideas or suggestions?

---

### Post by oolunchbox on 2006-04-03
when i ```
sudo fdisk -l
``` i get ```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8669    69633711   83  Linux
/dev/sda2            8670        9039     2972025    5  Extended
/dev/sda5            8670        9039     2971993+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      387621   195360952+  42  SFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      387621   195360952+  42  SFS

```

---

### Post by Sutekh on 2006-04-03
Edit: I have no idea what filesystem SFS is.  If they are NTFS, fdisk should have said so.  I don't know if the following instructin will work for SFS, whatever it may be.


To start you need to unmount them, as it sounds like they are currently mounted, just not in the place you want them.

You know the name of the NTFS partitions (/dev/sdb1, /dev/sdc1), so you can unmount them using
```
sudo umount /dev/sdb1
sudo umount /dev/sdc1
```

Then you can edit your /etc/fstab to set them up as automatically mounted partitions.

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Once you have opened the fstab then you need to add two lines to mount the drives. 

For NTFS partitions you should add lines similar to these
```
/dev/sdb1    /media/d   ntfs   nls=utf8,umask=0222   0   0
/dev/sdc1    /media/g   ntfs   nls=utf8,umask=0222   0   0
```
then save the file (Ctrl+O) and exit (Ctrl+X) and remount the partitions with```
sudo mount -a
```

---

### Post by oolunchbox on 2006-04-03
Thanks for the help, I've discovered that apparently when I borked the disks by trying to set them up as a JBOD RAID array.  I've since been able to get them mounted by repartitioning and formatting.  Unfortunately I've lost everything on the drives.  :(

---

