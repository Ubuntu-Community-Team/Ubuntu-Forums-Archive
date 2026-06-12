---
title: "Second Harddrive in Server"
date: 2010-10-10
forum: General Help
---

### Post by Abadon125 on 2010-10-10
Hi, I just installed Ubuntu 10.10 server on my server computer.  I have all my files on separate hard drives and am trying to find them (I am fairly new to linux)

These hard drives were unplugged during the installation.  After I was done installing I shut it down and plugged them in.  They are NTFS format.  Will they automatically mount?  If so where are they?
If they do not automatically mount how can I mount them?

Thanks! Sorry for the very basic question.

---

### Post by Abadon125 on 2010-10-12
Solved

sudo apt-get install ntfs-config
sudo fdisk -l | grep NTFS | awk '{print $1}'
sudo cp /etc/fstab /etc/fstab.orig
sudo vi /etc/fstab
Add the line
   <your partition> /media/<mount point> ntfs-3g defaults,locale=en_US.utf8 0 0
sudo umount <your partition>
sudo mount -a

Found at:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

