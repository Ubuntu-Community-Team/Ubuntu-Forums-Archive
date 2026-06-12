---
title: "Can't mounts Ipod on ubuntu lucid"
date: 2010-06-27
forum: General Help
---

### Post by crunchyx on 2010-06-27
I mistakenly unplugged my 4th Generation Ipod Nano while Rytmobox was transfering files, the ipod is working great but Ubuntu refuses to recognize it. I don't dee it anymore in /media and Rytmobox doesn't recognize it anymore.

Any help would be appreciated.



This is the result of sudo fdisk -l


> Disk /dev/sdf: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        1357     7783940    b  W95 FAT32
Partition 1 does not start on physical sector boundary.

---

### Post by dragos240 on 2010-06-27
Do this in a terminal:
 sudo fsck /dev/sdf1


It was just an unclean unplug, that should fix her!

---

### Post by dino99 on 2010-06-27
try:

sudo dpkg-reconfigure ipod

---

### Post by ashokiiit on 2010-06-27
im not sure about updates of rhythm box but there is a gud application called hippo ipod management tool.

Try it. cant guarantee it works :)

---

### Post by dragos240 on 2010-06-27
> **dino99 said:**
> try:

sudo dpkg-reconfigure ipod

I'm pretty sure that's only with packages.

---

### Post by crunchyx on 2010-06-27
> **dragos240 said:**
> Do this in a terminal:
 sudo fsck /dev/sdf1


It was just an unclean unplug, that should fix her!


```
me@me-laptop:~$ sudo fsck /dev/sdb1
[sudo] password for me: 
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Reclaimed 4 unused clusters (65536 bytes).
Free cluster summary wrong (0 vs. really 4)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 2093 files, 486246/486250 clusters
me@me-laptop:~$ 
```]

Didn't help.

---

### Post by dragos240 on 2010-06-27
> **crunchyx said:**
> ```
me@me-laptop:~$ sudo fsck /dev/sdb1
[sudo] password for me: 
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Reclaimed 4 unused clusters (65536 bytes).
Free cluster summary wrong (0 vs. really 4)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 2093 files, 486246/486250 clusters
me@me-laptop:~$ 
```]

Didn't help.

Okay, please try unplugging the device and rebooting, try it again, it should be fixed :)

---

### Post by crunchyx on 2010-06-27
> **dino99 said:**
> try:

sudo dpkg-reconfigure ipod


I installed ipod package then

```
me@me-laptop:~$ sudo dpkg-reconfigure ipod
me@me-laptop:~$ 
```

Also to no avail.

---

### Post by crunchyx on 2010-06-27
> **dragos240 said:**
> Okay, please try unplugging the device and rebooting, try it again, it should be fixed :)

Unplugged rebooted replugged, and still refuses to be recognized. (Though the ipod does show that it's connected to a computer as before)

---

### Post by dragos240 on 2010-06-27
> **crunchyx said:**
> Unplugged rebooted replugged, and still refuses to be recognized. (Though the ipod does show that it's connected to a computer as before)

Try fdisk -l again, and tell me if it works on another operating system. If it does, do this:

sudo mount /dev/sdf1 /mnt

if the command gives you errors, tell me them.

---

### Post by crunchyx on 2010-06-27
> **ashokiiit said:**
> im not sure about updates of rhythm box but there is a gud application called hippo ipod management tool.

Try it. cant guarantee it works :)
  
Installing [Hipo]("http://projects.gnome.org/hipo/#download") when I run it.

[IMG]http://img121.imageshack.us/img121/7562/screenshoteuz.png[/IMG]

Tried to search for org.freedesktop.hal in Synapic but wasn't very successful.

---

### Post by dragos240 on 2010-06-27
> **crunchyx said:**
> Installing [Hipo]("http://projects.gnome.org/hipo/#download") when I run it.

[IMG]http://img121.imageshack.us/img121/7562/screenshoteuz.png[/IMG]

Tried to search for org.freedesktop.hal in Synapic but wasn't very successful.

COULD NOT FIND HAL???? Oh yeah, ubuntu doesn't use HAL anymore. Installing hal may slowdown your boot-time by about 1-2 seconds, but it's very useful, install hal from the repo. Please, it will help you a lot, I don't know what canonical was thinking when they removed hal.

---

### Post by crunchyx on 2010-06-27
> **dragos240 said:**
> Try fdisk -l again, and tell me if it works on another operating system. If it does, do this:

sudo mount /dev/sdf1 /mnt

if the command gives you errors, tell me them.

Fdisk -l same as before

```
Disk /dev/sdb: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1357     7783940    b  W95 FAT32
Partition 1 does not start on physical sector boundary.
```


```
me@me-laptop:~$ sudo mount /dev/sdb1 /mnt
me@me-laptop:~$ 

```

I can access the files through /mnt but it doesn't show up on the desktop or in Rythmobox.

As soon as I'll have a windows PC I'll check it.

---

### Post by dragos240 on 2010-06-27
> **crunchyx said:**
> Fdisk -l same as before

```
Disk /dev/sdb: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1357     7783940    b  W95 FAT32
Partition 1 does not start on physical sector boundary.
```
```
me@me-laptop:~$ sudo mount /dev/sdb1 /mnt
me@me-laptop:~$ 

```I can access the files through /mnt but it doesn't show up on the desktop or in Rythmobox.

As soon as I'll have a windows PC I'll check it.

GOOD! That shows it's just a hal problem! Okay, do this, install hal. If that doesn't work, then do this:
rm -rf .gnome2. This will reset gnome's configuration to it's default values. Try using that.

---

### Post by crunchyx on 2010-06-27
> **dragos240 said:**
> COULD NOT FIND HAL???? Oh yeah, ubuntu doesn't use HAL anymore. Installing hal may slowdown your boot-time by about 1-2 seconds, but it's very useful, install hal from the repo. Please, it will help you a lot, I don't know what canonical was thinking when they removed hal.


Searched for hal I think it is installed.

[IMG]http://img294.imageshack.us/img294/8387/screenshot28oi.png[/IMG]

---

### Post by dragos240 on 2010-06-27
Do this:
sudo service hald start

hald is HAL-daemon.

---

### Post by crunchyx on 2010-06-27
> **dragos240 said:**
> GOOD! That shows it's just a hal problem! Okay, do this, install hal. If that doesn't work, then do this:
rm -rf .gnome2. This will reset gnome's configuration to it's default values. Try using that.

Removed .gnome2 didn't help

I can only access the ipod files after this

```
sudo  mount /dev/sdb1 /mnt
```

as in here after mounting

[IMG]http://img156.imageshack.us/img156/8938/screenshot200.png[/IMG]


Thanks for the continuous trying.

---

### Post by crunchyx on 2010-06-27
> **dragos240 said:**
> Do this:
sudo service hald start

hald is HAL-daemon.


```
me@me-laptop:~$ sudo service hald start
hald: unrecognized service
me@me-laptop:~$ 
```

---

### Post by dragos240 on 2010-06-27
> **crunchyx said:**
> ```
me@me-laptop:~$ sudo service hald start
hald: unrecognized service
me@me-laptop:~$ 
```
Try hal instead, it sometimes varies. If it doesn't exist, reinstall hal.

---

### Post by crunchyx on 2010-07-01
I ended up reformatting the ipod (after backing up all music) in itunes (on win xp).

---

