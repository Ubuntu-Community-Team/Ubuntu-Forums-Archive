---
title: "Ubuntu Disk Utility"
date: 2010-05-12
forum: General Help
---

### Post by bluestreek on 2010-05-12
The disk utility is not working properly for me in Ubuntu 10.04 LTS. It takes a long time to load and then shows nothing in the list. Randomly it will just start working again. I saw another report of this on launchpad but I cannot seem to find it anymore.

Any help would be great!

---

### Post by blazemore on 2010-05-13
Hi, could you please post a screenshot of the problem in action if possible?
Does this happen every time?
What steps do you have to take to reproduce the bug?

---

### Post by tommyjek on 2010-05-18
Hello! I have a similar problem. Mine Disk Utility is not starting at all. Aditionaly my drives are not listed in "Places", but i can manually mount some of them. USB, and CDs do not automount. I think these problems are related.
Problem so far:
- I dont have Disk Notifications daemon in process list (think it should be there) although i have it enabled in startup list
- when i try to run it manually this is an error: 
   **
   libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)
   Aborted
-i get the same error when executing command "palimpsest", Disk Utility

please help,
thank you

---

### Post by bluestreek on 2010-05-19
Its just totally empty.  Also -

administrator@administrator-desktop:~$ palimpsest

(palimpsest:1816): libgdu-WARNING **: Couldn't get daemon properties
Error creating pool: `(unspecified error)'

(palimpsest:1816): Palimpsest-CRITICAL **: Bailing out
administrator@administrator-desktop:~$

---

### Post by tommyjek on 2010-05-20
I menaged to solve my problem. Booted with some CD in my drive, and hop, drives were in 'Places', except 1 partition. i could open Disk Utility also and there was something wrong with that partiton, it was supposed to be NTFS but instead there were something W95... GParted reported it as regular NTFS partition. So I removed that and created new one NTFS, and since then everything is working ok.

---

### Post by repsakkgn on 2010-07-12
same here. Latest updates installed and no automount present.
palimpset in console gives
libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)
What should I do?

---

### Post by herophuong on 2010-07-21
Same for me! Any ideas?

---

### Post by MooPi on 2010-07-21
I don't use palimpset so I can't speak to that issue. I do use gparted and have never been disappointed with its performance.

---

### Post by herophuong on 2010-07-21
I found one thing: I must have plugged an usb before start palimpset.

---

### Post by tomski on 2010-08-18
the thing that irks me is the total lack of documentation of palimpsest Disk Utility
i mean on the gnome webbvy there is 2 sentances and one screen shot but the features this has are advanced yet no explanation for what they actually do !

i have 1 ntfs partition which is being reported as 'unkown' palimpsest has a feature to 'edit' partiton & change info but i cannot find a report of what this does from anywhere & dont want to loose data

also there is no man page for it either so it may look nice and funky but i am not using it at all until i see more documentation

currently i use ultimate boot cd or hirens boot cd depending on what i want to do and with them 2 cd i have recovered tb's of data for friends & work collegues

---

### Post by jpmonette on 2010-12-17
I have the same problem:

```
jpmonette@azerox:~$ palimpsest 
**
libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)
Abandon
```

Here is more information about how I ended up with this error message:

[LIST=1]
[*]I installed TinyXP on the same logical partition then Linux
[*]I booted on the Ubuntu Live CD to fix GRUB2. I went into palimpset and the partitions weren't right, but it was working
[*]I executed sudo os-prober && sudo grub-install ...
[/LIST]
I'm pretty sure it came after installing TinyXP. I think my computer is not able to mount the other partitions anymore. When I go in gparted, I can only see a giant /dev/sda. 

When I do fdisk -l, it returns nothing.

And where's what happen with fdisk /dev/sda

```
jpmonette@azerox:~$ fdisk /dev/sda

Impossible d'ouvrir /dev/sda
```

Thanks for the help.

---

### Post by Mikhail Titov on 2011-07-28
A patch has been proposed. Testers needed [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038)

---

