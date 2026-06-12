---
title: "Need Help Sharing 2nd &amp; 3rd Physical Drives"
date: 2010-11-10
forum: General Help
---

### Post by onaridge on 2010-11-10
I have a Dell XPS with Ubuntu 10.04 installed. I have a laptop dual booting Windows 7 and Ubuntu 10.04. I can see all shared folders on the Dell from my Windows partition in my laptop but can only see the shared folders in Home on the Dell from my Ubuntu partition in the laptop. My set up is as follows:

Dell:

root, home and swap are on the 1st 160g hard drive. 
2nd 160g hard drive has only the one partition: /storage1
3rd hard drive, 500g has only one partition: /storage2

I cannot access any of the shares on either storage drive but I can see them from the ubuntu laptop. What I want to do is have access to those storage drives from my laptop. If I go into Nautilus, navigate to either storage drive, I cannot share them via right click, properties because I don't have root. Basically I am not sure how to go about this. There are a few folders in storage 1 and storage 2 that I want to be able to access from my Ubuntu partition in my laptop. This is one of the reasons I still have Windows on the other laptop partition but I really would like to dump it.  Samba is installed and I tried giving permissions that way. It allowed me to add the drives but it had no effect.

---

### Post by onaridge on 2010-11-11
nobody can help me? :-(((((((((

---

### Post by plucky on 2010-11-12
See [Mounting Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux) for mounting your /storage1 and /storage2 partitions.

If you follow the tutorial correctly you should then become the owner of the partitions and it will be then simple to share the partitions using samba and the right click sharing option.


Good Luck

---

### Post by onaridge on 2010-11-12
My Fstab already has this, so do I just uncomment the two lines that have Storage 1 and storage 2 respectively? Looks like the work has sort of already been done but not fully. They have been mounted I just need to CHMOD them? I should add that a tech installed this system for me which is why it looks like it was partially done. (I decided to dump windows after a major virus infection and he convinced me to let him install Ubuntu.)

Fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=05968c3f-a14e-4aba-afa9-1ff1de84615b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=7b42a328-a86e-4322-a1f1-921fc86eb14b /home           ext4    defaults        0       2
# /storage1 was on /dev/sdb1 during installation
UUID=b4162ca1-4dc5-44f7-b4b6-a32c89798a5a /storage1       ext4    defaults        0       2
# /storage2 was on /dev/sdc1 during installation
UUID=0a9e8e0d-7c76-4a82-b4da-8e500cace4a0 /storage2       ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=01cd8877-13cb-4b23-adf3-226fc70dcee8 none            swap    sw              0       0

This is the result of ls -l /dev/disk/by-uuid :

loren@loren-linux1:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-11-11 16:55 01cd8877-13cb-4b23-adf3-226fc70dcee8 -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-11-12 00:17 0497-DFBE -> ../../sdd1
lrwxrwxrwx 1 root root 10 2010-11-11 16:55 05968c3f-a14e-4aba-afa9-1ff1de84615b -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-11-11 16:56 0a9e8e0d-7c76-4a82-b4da-8e500cace4a0 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-11-11 16:55 7b42a328-a86e-4322-a1f1-921fc86eb14b -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-11-11 16:55 b4162ca1-4dc5-44f7-b4b6-a32c89798a5a -> ../../sdb1

---

### Post by onaridge on 2010-11-12
With the help of another forum post I solved this and the solution was an easy one. gksudo nautilus, then navigated to folders, applied the permissions. Voila, works!

---

