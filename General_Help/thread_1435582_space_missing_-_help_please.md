---
title: "space missing - help please"
date: 2010-03-21
forum: General Help
---

### Post by rajanm1 on 2010-03-21
i have ubuntu 8 - hardy and i just installed a program that does automatic backups but filled my tiny netbook's 8GB. i didn't  realise it done it automatically until it started crashing which i thought was wierd and so i checked my hdd space and it was all used up! i have stopped the program and tried to remove the backup files to create some more space but i used nautilus and not the files have gone but the amount of free space has not changed....:confused:

anyone know how i can get my space back please?


on a seperate issue, why does it show up that i have two seperate hdd's with the same amount of space? (on system monitor the 1st device is /dev/sda2 and the other is gvfs-fuse-daemon)


thanks

---

### Post by darolu on 2010-03-21
Check your "/home/<username>/.gfvs" folder (considering  you mentioned gvfs-fuse-daemon), it is a hidden folder when you open Nautilus press Ctrl+H to view hidden elements (press it again to hide them back); the back up application probably created a virtual disk and it is in this folder.

The separate partitions with the same amount of space is most likely your Extended partition and a partition in it, for example your swap partition which would be /dev/sda2 Extended and /dev/sda5 swap, although the gvfs daemon displaying as a HD/Partition is weird. The virtual disk is probably mounted to your ~/.gfvs folder, go to Applications - Accessories - Terminal and type this in:
```
$ mount
```
Paste your result.

---

### Post by rajanm1 on 2010-03-21
> **darolu said:**
> Check your "/home/<username>/.gfvs" folder (considering  you mentioned gvfs-fuse-daemon), it is a hidden folder when you open Nautilus press Ctrl+H to view hidden elements (press it again to hide them back); the back up application probably created a virtual disk and it is in this folder.

The separate partitions with the same amount of space is most likely your Extended partition and a partition in it, for example your swap partition which would be /dev/sda2 Extended and /dev/sda5 swap, although the gvfs daemon displaying as a HD/Partition is weird. The virtual disk is probably mounted to your ~/.gfvs folder, go to Applications - Accessories - Terminal and type this in:
```
$ mount
```Paste your result.

result (that didn't work so i just typed mount):
rajan@rajan:~$ mount
/dev/sda2 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-lpia/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rajan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rajan)


the gfvs was empty, the backup program was called either simple backup or keep (most like the 1st) and did not create a separate partion but saved them to a folder called /var/backup.
my netbook is a dell mini 9 with only "8GB" of onboard space which works out to be 6.9GB real and the  /dev/sda2 and the gvfs-fuse-daemon both have 6.9GB of space on them each so don't think that there is a partion

any more ideas?

---

### Post by darolu on 2010-03-21
No there is not a partition, what the backup program most likely did, is create a Virtual Disk and mount it to ~/.gfvs; the gfvs-fuse-daemon mounts it there just like it does with a (i.e.) network-shared item.

Anyways, the program is SimpleBackUp, and you can use it to delete all the back up files it already created or configure how your back ups are made, for example, you can set it to back up your files using other media (like pendrives or external hard drive) read this link, it may help you do it: [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

If you want to do it manually, unmounting this virtual drive may be needed in order to delete the virtual disk (if it indeed created one as I believe), the "mount" command will tell you where it is mounted; delete the virtual disk from /var/backup to delete it you will need root privliges, to get them press ALT+F2 and type "gksu nautilus" in (no quotes).

---

### Post by rajanm1 on 2010-03-22
> **darolu said:**
> No there is not a partition, what the backup program most likely did, is create a Virtual Disk and mount it to ~/.gfvs; the gfvs-fuse-daemon mounts it there just like it does with a (i.e.) network-shared item.

Anyways, the program is SimpleBackUp, and you can use it to delete all the back up files it already created or configure how your back ups are made, for example, you can set it to back up your files using other media (like pendrives or external hard drive) read this link, it may help you do it: [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

If you want to do it manually, unmounting this virtual drive may be needed in order to delete the virtual disk (if it indeed created one as I believe), the "mount" command will tell you where it is mounted; delete the virtual disk from /var/backup to delete it you will need root privliges, to get them press ALT+F2 and type "gksu nautilus" in (no quotes).

i was able to delete the backups from the backup folder as i think i mentioned in my first post using gksu nautilus HOWEVER although the files no longer appear to be there there is no more free space then before i deleted them :oops:

---

### Post by rajanm1 on 2010-03-22
do i have to completely reinstall ubuntu?  can i do this with an external usb dvd drive? as there isn't an internal one.

---

### Post by xhalarin on 2010-03-22
An external USB-DVD drive should work fine.  You might have to press F12 or a similar key or go into your systems bios to get it to boot from there.  

Reinstalling shouldn't be necessary though.

Have you tried the Disk Usage Analyzer to drill in on where the disk space is being used?

You also would want to empty your Trash (I'm sure you did that already) but also the trash of the root user if you haven't.  See this post for instructions:
[http://ubuntuforums.org/showthread.php?t=1434102](http://ubuntuforums.org/showthread.php?t=1434102)

---

### Post by rajanm1 on 2010-03-27
cheers, but i am the only user (so would guess i am the root user aswell?) and the Disk Usage Analyzer tells me where all of the data is but these is still loads missing (it all doesn't add up... :-s

---

### Post by rajanm1 on 2010-03-27
FINALLY FREE AND PROBLEM SOLVED!!!!

thanks for that link, i had a major read through it and found out that there was still a lot of backup data in root/.local/share/Trash which you can't see unless you use nautilius to PERMANENTLY delete it because what i did was just use nautilius to delete it (not permanently delete it) so it was still stored there!!

 "sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort" showed this so all happy now :p

---

