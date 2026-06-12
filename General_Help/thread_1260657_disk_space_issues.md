---
title: "disk space issues"
date: 2009-09-07
forum: General Help
---

### Post by analogorithm on 2009-09-07
my update manager has a bunch of uploads for me and when i try to install them i'm told there is not enough disk space, also when i try to download anything through my bittorrent i get a similar message.  i'm new to ubuntu and could use some suggestions with this problem. thank you for any help

---

### Post by Efwis on 2009-09-07
could you open terminal and put
```
df -h
```
then copy and paste what it says in your next reply.

---

### Post by drs305 on 2009-09-07
analogorithm,

Welcome to Ubuntu and the Ubuntu forums.  :P

When you say you are new, did you just install Ubuntu, and did you select "side by side" with Windows?

I ask because there is a bug affecting new users who installed Ubuntu this way. It results in a system partition ( / ) that is too small to function correctly.

You can tell by running this command in a terminal:
```

df -Th

```
If you see the root partition is 2.3-2.5 GB, you will have to either reinstall Ubuntu or expand your / partition by taking space from another partition.

I've written some guides that can help:

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

If you have a normal partition size (10GB+) and want to find out what is taking up so much space, refer to this guide:
[Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Sorry you are having these problems as a new Ubuntu user but we will help you get this working.

---

### Post by fluffman86 on 2009-09-07
Your Ubuntu partition--the part of the hard drive that it lives on--is too small.  

If you installed with the Wubi installer INSIDE of windows, then let us know so someone else can help.

If you did a normal install from the live cd and installed it alongside windows, then you need to:
1. Download, install, and run [ccleaner](http://ccleaner.com)
2. defragment Windows
3. Find out how much free space you have now from My Computer
4. boot into the live CD again
5. Go to System > Administration > Partition Editor
6. Click your Windows parition (look for "ntfs")
7. Click resize/move at the top and make it smaller, but be sure you only make it smaller by the amount of free space you have in windows. Leave yourself a MINIMUM 3GB buffer, preferably 5 or more if possible.  If this is not possible, *DO NOT PROCEED!*
8. Click Resize/Move to save those changes temporarily.
9. On the main Gparted screen now, click your Ubuntu parititon (look for ext3) and make it larger so it takes up the space that was freed by windows.
10. Click apply and wait a very long time for this process to complete.

---

### Post by analogorithm on 2009-09-08
ok i copy and pasted the command you all gave me and my partition size is too small.  i will be reinstalling off my cd now.  i did not do the installation alongside windows because windows finally broke me.  i couldn't handle the worms slowing me down and viruses crashing my system once a year.  i will update in a little while as to how the reinstall works out.  thank you all for your quick and very useful replies.

---

### Post by analogorithm on 2009-09-08
ok after the reinstall i now get this when i input the command into the terminal

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    222G  2.1G  209G   1% /
tmpfs        tmpfs    1.4G     0  1.4G   0% /lib/init/rw
varrun       tmpfs    1.4G  104K  1.4G   1% /var/run
varlock      tmpfs    1.4G     0  1.4G   0% /var/lock
udev         tmpfs    1.4G  160K  1.4G   1% /dev
tmpfs        tmpfs    1.4G  764K  1.4G   1% /dev/shm
lrm          tmpfs    1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile


i discovered the problem was i originally installed my friends ubuntu 8.1 and when i got the newer version i accidentally installed it alongside the old.  my stupid mistake and again thank you all for helping so quickly.

---

