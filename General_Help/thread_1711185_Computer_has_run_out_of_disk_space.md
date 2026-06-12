---
title: "Computer has run out of disk space"
date: 2011-03-21
forum: General Help
---

### Post by jw62822000 on 2011-03-21
I installed Maverick Meerkat along with Windows 7 for dual booting. I created a partition of around 68 Gb to install it on. After using about 15 Gb of it, it told me that I only had a few hundred megabytes left, when I actually have over 50 gigabytes left. This is what Disk Usage Analyzer and GParted show
[SIZE=1][[IMG]http://i977.photobucket.com/albums/ae257/jw6282000/Screenshot.png?t=1300680360[/IMG]]("http://i977.photobucket.com/albums/ae257/jw6282000/Screenshot.png?t=1300680360")[/SIZE][[IMG]http://i977.photobucket.com/albums/ae257/jw6282000/Screenshot--dev-sda-GParted.png?t=1300680632[/IMG]]("http://i977.photobucket.com/albums/ae257/jw6282000/Screenshot--dev-sda-GParted.png?t=1300680632")

---

### Post by troll1602 on 2011-03-21
Could you provide a few more details with how you setup your install. Perhaps you followed a how-to?

A few things that look *funny* to me: 1)the folder called "host" and how large it is, and 2) it looks like you installed Ubuntu on /dev/sda1 ? I'm a little confused because both partitions are formated as NTFS. When you install Ubuntu 10.10 the default drive format is ext4.

---

### Post by jw62822000 on 2011-03-21
When I had Windows 7 on a single drive, I noticed that there was a recovery partition about 15 GB in size. Windows didn't let me use this even though it was empty, so I used a third party program to divide the memory. I installed Ubuntu it with Wubi after making a partition and formatting it to NTFS. I'm guessing "host" is where the os is installed, because it said the installation size was 8 GB on wubi. I also have no idea why there is 2.49 MB of unallocated memory.

---

### Post by troll1602 on 2011-03-21
Searching through the forum, it looks like a couple others have had this same issue with installing through wubi on a separate partition. This is a *strange* way to install Ubuntu. When you install with wubi you are not "dual-booting" exactly because you don't have to create a separate partition.

So, here is what I would do. First, backup all of your important files on both windows and ubuntu (windows just in case, but definitely ubuntu because those files will be deleted either way). Then, I would do one of two things:
1) remove ubuntu from windows, like any other windows application. Merge the partitions and then reinstall ubuntu through wubi. 
Or 2) remove ubuntu from windows, keep the two partitions and do a normal dual-boot. This requires downloading ubuntu, from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"). Follow the instructions there and during the install you need to select the correct partition to install ubuntu onto.

Post back with questions and remember to "read twice and partition once." Making random or incorrect partitions can potentially screw up either OS!

---

### Post by jw62822000 on 2011-03-21
Thanks for the reply. I have one more question. If I copy my whole root directory to an external hdd and reinstall ubuntu, will I be able to copy over my previous root to the new installation to restore all my software and settings?

---

### Post by bcbc on 2011-03-21
[HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

Copy the \ubuntu\disks\root.disk file. it's 8GB (from what you said) and it's possible to restore from it later.

---

### Post by troll1602 on 2011-03-21
That wubi migration how-to looks pretty good. If you are still interested in a backup/restore how-to check out this post:
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by jw62822000 on 2011-03-21
Thanks for all the help guys. I really appreciate it.

---

