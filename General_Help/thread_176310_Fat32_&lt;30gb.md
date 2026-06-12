---
title: "Fat32 &lt;30gb"
date: 2006-05-14
forum: General Help
---

### Post by tris203 on 2006-05-14
I know there is a FAT32 limit of 32gb in one partition. But i have a 200gb hd. I have patitioned it so that:

5gb - FAT32 - WINDOWS
5gb - FAT32 - Ubuntu
176GB - RAW - Files

how can i make the 176gb partition formated to FAT32 so that linux can access my files too, without partitioning it into several smaller partitions.


Thanx

tris203

---

### Post by cgjones on 2006-05-14
You can format it in Ubuntu using the command line or better yet, a program such as GParted. Linux doesn't suffer from the 32GB limit that Windows imposes on you.

---

### Post by aysiu on 2006-05-14
I've had a 120 GB FAT32 partition.

There's no 30 GB limit. I don't know where you read that, but it's wrong.

There is, however, a 4 GB *file size* limit in FAT32. You cannot store DVD images on FAT32, as they're too big.

---

### Post by cgjones on 2006-05-14
**tris203**: I just noticed that you have the Windows and Ubuntu partitions as FAT32. They should be NTFS for Windows (depending on the version you are using) and EXT3 or ReiserFS for Ubuntu. Using FAT32 for the OS partitions prevents the operating systems from setting permissions and stuff like that.

**aysiu**: In Windows 2000 and XP, there is a limit of 32GB when creating a FAT32 partition. Windows can handle partitions larger then that just fine, it just won't let you create one.

---

### Post by aysiu on 2006-05-14
[QUOTE=cgjones]
**aysiu**: In Windows 2000 and XP, there is a limit of 32GB when creating a FAT32 partition. Windows can handle partitions larger then that just fine, it just won't let you create one.[/QUOTE] Ah, but FAT32 partitions can be created from Linux.

In any case, you don't need FAT32. Just use [http://www.fs-driver.org/](http://www.fs-driver.org/) to read/write Ext3 from Windows--I've used it before, and it works fine.

This is what I would do:
5gb - NTFS - WINDOWS
5gb - Ext3 - /
176GB - Ext3 - /home

---

### Post by tris203 on 2006-05-15
[QUOTE=aysiu]Ah, but FAT32 partitions can be created from Linux.

In any case, you don't need FAT32. Just use [http://www.fs-driver.org/](http://www.fs-driver.org/) to read/write Ext3 from Windows--I've used it before, and it works fine.

This is what I would do:
5gb - NTFS - WINDOWS
5gb - Ext3 - /
176GB - Ext3 - /home[/QUOTE]

Will i be alright to set my /home directory to ext3 as i want that partition available to windows and linux.

sorry to sound like a n00b. ;) :oops:

---

### Post by aysiu on 2006-05-15
[QUOTE=tris203]Will i be alright to set my /home directory to ext3 as i want that partition available to windows and linux.

sorry to sound like a n00b. ;) :oops:[/QUOTE] Yes, you'll be all right if you install [http://www.fs-driver.org/](http://www.fs-driver.org/) in Windows, which allows you to access Ext3 from Windows.

---

### Post by tris203 on 2006-05-15
Awsome, il try that now!

---

