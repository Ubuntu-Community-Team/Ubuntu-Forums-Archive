---
title: "Gaining permissions on my second hard drive"
date: 2009-11-27
forum: General Help
---

### Post by mattsid1 on 2009-11-27
I've googled this 'problem' and have found a ton of posts from people with similar problems, but still not quite sure how to solve it.

I recently installed a second hard drive on my PC and it has no problems recognizing it and mounting it. However when I try to copy files over to it I get the "you do not have permissions to create it in the destination" message.

I am aware that this is related to security and don't want to mess around with that, but am a bit confused why I can't access it since  I don't have anything on it. Is there a way around it?

Here is the output from my fstab and fdisk.

fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b413cab1-4e2d-4b24-b3eb-4e278c8267c6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fa5fc8e2-c842-448b-b20b-cbc02e56b9e2 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=c27a8bb6-c40b-44dd-95a4-1bbd5e95bc49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/ttyACM0 /mnt/phone auto noatime,rw,users,exec,uid=1000,gid=100 0 0
/dev/sdb1 /media/newhome ext3 defaults 0 0


fdisk

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b413cab1-4e2d-4b24-b3eb-4e278c8267c6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fa5fc8e2-c842-448b-b20b-cbc02e56b9e2 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=c27a8bb6-c40b-44dd-95a4-1bbd5e95bc49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/ttyACM0 /mnt/phone auto noatime,rw,users,exec,uid=1000,gid=100 0 0
/dev/sdb1 /media/newhome ext3 defaults 0 0

---

