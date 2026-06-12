---
title: "There is not enough space on the destination"
date: 2012-02-07
forum: General Help
---

### Post by ahmedo047 on 2012-02-07
I am using Ubuntu 11.1. I am trying to copy a folder (8 GB) on the desktop from portable disk but I get this error:
"There is not enough space on the destination. Try to remove files to make space"
   But there is free space (400 GB) on disk (I look at from "Disk Usage Analyser").
How can I fix this problem?

---

### Post by SuaSwe on 2012-02-07
Hi ahmedo047,

What folder are you trying to copy the file to? Could it be that this folder is mounted on a small partition without enough space to accommodate the file? Perhaps it would be worth trying to carry out the steps in Terminal and pasting them here so that we can get a better idea of what's happening:

```

df -h
cp /media/USBdrive/file-to-move /home/user/Desktop

```

Where 'df -h' will tell us of what's mounted where and at what size, /media/USBdrive/filee-to-move is the location of the file on the USB drive (the USB drive will be listed in df -h and mounted on /media) and /home/user/Desktop the location you're attempting to copy the file to.

---

### Post by ahmedo047 on 2012-02-08
I tried that "SuaSwe" said. I get the same error again :( I am trying to copy a folder on the desktop.

---

### Post by jamesisin on 2012-02-08
Does your System Monitor (or df) show that you have enough space on your / (or /home if they are separate) partition?

---

### Post by pixiq on 2012-02-08
Please cut and paste the output of the command 
```
df
``` into 'this editing window' and post it in order for us to see.

And explain from which partition and to which partition you want to copy! Are you allowed to copy to that partition at all? (Try with a small file!)

Run this command to show the size of what you want to copy
```
du 'source-folder'
``` of course entering the real name of the folder. Also please post the output of this command. Mark the text with CODE tags using the icon # at the top of this window.

If your system is new enough, you can use the -h (human-readable-option)

```
df -h
du -h 'source-folder'
```

---

### Post by ahmedo047 on 2012-02-08
```
ahmedo@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0            17884496  10774144   6201860  64% /
udev                   3050752         4   3050748   1% /dev
tmpfs                  1223468       812   1222656   1% /run
none                      5120         0      5120   0% /run/lock
none                   3058664      1372   3057292   1% /run/shm
/dev/sda2            488282108  34905512 453376596   8% /host
/dev/sdb1            244128000  58799648 185328352  25% /media/SAMSUNG
```Furthermore
```
ahmedo@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             18G   11G  6.0G  64% /
udev                  3.0G  4.0K  3.0G   1% /dev
tmpfs                 1.2G  812K  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.0G  1.4M  3.0G   1% /run/shm
/dev/sda2             466G   34G  433G   8% /host
/dev/sdb1             233G   57G  177G  25% /media/SAMSUNG

```I want to copy on the desktop the folder called "a" from portable disk (/media/SAMSUNG).

```
ahmedo@ubuntu:~$ cd /media/SAMSUNG
ahmedo@ubuntu:/media/SAMSUNG$ du 'a'
.....
6240    a/biy
7485696    a

``` From System Monitor:
  System Status
  Available diskspace:438.3 GiB


You asked "Try with a small file!" Yes. I tried it. I dont have any problem. 



Furhermore:
From Disk Usage analyzer:
_Folder _     _Usage_    _Size_         _Contents_
home       100%   8.3 GB    1 item
  ahmedo  100%   8.3 GB    37 items

---

### Post by Cheesemill on 2012-02-08
There is not enough space on the destination.

You only have 6GB of free space on / which is where you are trying to copy to.

---

### Post by jamesisin on 2012-02-08
Like Cheesemill wrote you only have 6 GB on / (I'm assuming /dev/loop0 means you are using Wubi?).  The location /host is your host computer (presumably Windows) and that is technically outside of / as would be /media/SAMSUNG which is presumably some USB connected drive or similar.  You ought to be able to access files in /host if you'd rather move/copy the file somewhere onto your Windows machine.

---

### Post by pixiq on 2012-02-09
> **jamesisin said:**
> Like Cheesemill wrote you only have 6 GB on / (I'm assuming /dev/loop0 means you are using Wubi?).  The location /host is your host computer (presumably Windows) and that is technically outside of / as would be /media/SAMSUNG which is presumably some USB connected drive or similar.  You ought to be able to access files in /host if you'd rather move/copy the file somewhere onto your Windows machine.
+1
Seeing the output of your commands, I agree, that there is not space enough on / but you can copy it to some directory in /host

When you feel comfortable with Ubuntu, I suggest that you consider 'dual boot' with Ubuntu on its own partition instead. You can browse the Ubuntu Forums and find several threads describing and discussing how to install Ubuntu to make a dual boot system.

---

