---
title: "Yet another permissions/ownership question"
date: 2010-01-06
forum: General Help
---

### Post by t3ddyg on 2010-01-06
I recently switched from windows to ubuntu, and am having problems sharing my files with samba for the remainder of my windows computers.  I had my drive setup with 2 NTFS partitions - 1 was the OS partition, and 2 was strictly my files.  When I switched to Ubuntu, I deleted partition 1, and installed ubuntu to the free space.  

First, I set my fstab to automount the NTFS partition.  I then installed samba.  When I right click on my NTFS files partition, and select sharing options - share this folder, i get a prompt saying "Nautilus needs to add some permissions to your folder "Files" in order to share it".

I select "add the permissions autmatically", and receive the error "Could not change permissions of folder Files".

Is there someway to change the ownership/permissions of the entire partition?  I got rid of windows.  I want ubuntu to hold the ownership/permissions controls.

This is a copy of my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=494d48ae-af62-4c28-8ae8-68f2cac0a39e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e6f647f0-8333-4173-ad78-eee9e4b09271 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/Files ntfs defaults,umask=007,gid=46 0 0
```

Any suggestions?  I tried a bunch of different things that turned up with the search.. but none got rid of the error message.

---

### Post by jonest1 on 2010-01-06
Please run the following command and give the output in a reply.

```
ls -ld /media/Files
```

Did you run nautilus as the root user when you tried to change the permissions?  ie: 'gksu nautilus'

---

### Post by t3ddyg on 2010-01-07
The output is as follows:
```
myname@mycomputer:~$ ls -ld /media/Files
drwxrwx--- 1 root plugdev 4096 2010-01-05 21:01 /media/Files

```

I found a post instructing me to run "sudo nautilus".  I was successfully able to share a subfolder in the partition using this method... but there was no option to share the entire partition.  I'm sorry if I'm missing something obvious.

Side question:  Would this be simpler if I just converted the entire partition to ext3? Would that be the best file system to convert to, or ext4?  I tried looking at the partition with gparted....but couldn't find any option to convert the drive's filesystem.

---

### Post by jonest1 on 2010-01-08
When creating file shares, it is best to think of it as sharing a directory instead of sharing a partition.  Normally, my suggestion would be to create subdirectories in the partition you wanted to use for sharing and share from there.  This will get you away from any issues about having mount permissions and ownership correct.  In unix, the default is for root to do the mounting and have ownership, which can be a good general security practice.

If you do not need to access the partition directly from a windows installation, it is best to format in ext3 or ext4.  I have not done the conversion from ext3 to ext4 before, but you can google it and I found this article which may be of use.

[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

---

