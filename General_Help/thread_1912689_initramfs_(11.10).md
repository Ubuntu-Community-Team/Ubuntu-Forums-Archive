---
title: "initramfs (11.10)"
date: 2012-01-21
forum: General Help
---

### Post by iyke=T on 2012-01-21
Hi All,

I upgraded my system installed with wubi in XP to 11.10. Accidentally the machine was witched with normal power down. Now on booting it says:

mount: mounting /dev loop0 on /root  failed: invalid arguement
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys  on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system dosen't have requested /sbin/init
No init found. Try passing init=bootarg

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built in commands

(initramfs)_

I have booted up with live cd 11.10 and 11.04 
tried:
 fsck /dev/sda

got errors of invalid block applied the code below

sudo ln -s /usr/bin/ntfsfix /sbin/fsck.ntfs sudo ln -s /usr/bin/ntfsfix /sbin/fsck.ntfs-3g

did not get any errors and tried

e2fsck with block numbers all could not get the machine to boot from HD


Pls any suggestions.

---

### Post by varunendra on 2012-01-21
Have you tried to boot into XP, use chkdsk -f on the WUBI installation partition (usually C: ), shut it down normally, and retry booting ubuntu?

Also, after running chkdsk, make sure the **\Ubuntu\disks\root.disk** file is in its place.

This blog by bcbc may be interesting for you: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by iyke=T on 2012-01-21
I did that with the f and v switch no problems. When I boot with a live cd I can see ubuntu folder with the root disk, swap disk and all the initr.img from kernel 2.6.28-11 to current 3.0.0-15. The only problem is that all of them display the message earlier and hangs. Haver seen such before. 

May be it is a problem with the /dev/loop0 because it first showed an error message and I remember it was about being full some time ago but I forgot to do something about it.

I am thinking of creating a new /dev/loop0 folder just to see. Really trying out any thing that can help me boot into the system then go from there.

---

### Post by bcbc on 2012-01-21
Don't try random stuff. That's going to lead to other issues.

How about running[ fsck on the root.disk]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F"). (It fixes the ext4 file system on the root.disk, you can't run it on your drive /dev/sda or on your partitions with the ntfs file system - as varunendra said you need to run chkdsk for that)

/dev/loop0 is a loop device resulting from loop mounting the root.disk. So creating /dev/loop folders isn't going to do anything there either.

Also, where exactly during the upgrade process did you turn off the computer?

---

