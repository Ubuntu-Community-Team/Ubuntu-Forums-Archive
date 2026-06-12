---
title: "How to stop the splash screen 'can't mount /dev/md0' press ......."
date: 2010-11-14
forum: General Help
---

### Post by byb3 on 2010-11-14
Hi everyone,

I've set up a RAID6 array with a normal hard disk (/dev/sda) for boot.  However whilst rebooting the computer I noticed that ubuntu is booting into a splash screen asking me:

Can't mount /dev/md0 (which is my RAID6 array) Press s to skip, c to continue, something along those lines....

The reason for this is that one of the drives from the RAID6 array was showing Uncorrectable read errors towards the end of the disk.  Something I was unaware of.  I'm in the process of replacing this.

As this server is completely headless (all I have remotely is SSH), I had to plug in a monitor and keyboard to find out that all I had to do was press S to get it to boot.  Wasted around an hour for that!

So my question is, how do I get Ubuntu to stop automatically trying to mount /dev/md0 before it boots?  Booting so that I can get SSH access is more important than getting the raid drive.  

Here is my /etc/fstab file (note I've put a # in front of /dev/md0, sdg1 and sdh1 are external ESATA drives, UUID is the swap):

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sdg1       /mnt/backup     ext4    defaults        0       0
/dev/sdh1       /mnt/spare      ext4    users,atime,rw,nodev,noexec,nosuid      0       0
#/dev/md0       /mnt/raid       ext4    defaults        0       0
# swap was on /dev/sda5 during installation
UUID=5ddd9034-628f-4ce0-99ce-968b6152ff23 none            swap    sw              0       0

Thanks in advance.

---

### Post by sohlinux on 2010-11-14
if you comment out /dev/md0 it will not mount at boot

---

