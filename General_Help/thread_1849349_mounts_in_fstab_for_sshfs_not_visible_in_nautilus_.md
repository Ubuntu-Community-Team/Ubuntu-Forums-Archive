---
title: "mounts in fstab for sshfs not visible in nautilus in ubuntu natty 11.04"
date: 2011-09-24
forum: General Help
---

### Post by borivoje on 2011-09-24
So the problem is as follows:

I created ssh keys and set up ssh to login without passwords. It worked. 
Then I added sshfs commands in fstab in order to connect my desktop and my laptop pc to share folders
When I save fstab file no device is added to my nautilus devices list. I did that in previous versions, nut now it simply doesn't work.

Help!

---

### Post by borivoje on 2011-09-24
Here's my fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=b0c479f7-2427-4d17-8e3c-b418919e6953 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda6 during installation
UUID=629e942a-310e-4439-b37c-d93c6ead6991 none            swap    sw              0       0
sshfs#borivoje@192.168.1.100:/home/borivoje /home/borivoje/boki-desktop fuse defaults,idmap=user,noauto 0 0

---

### Post by borivoje on 2011-09-24
It doesn't work with external usb hard drive either (I mean when I put it is fstab).

---

### Post by borivoje on 2011-09-24
Bump.

I know this is stupid because this usually works.

---

### Post by b0b138 on 2011-09-25
Have you rebooted or run mount -a after editing fstab? 

Did you add your user to the fuse group?

---

