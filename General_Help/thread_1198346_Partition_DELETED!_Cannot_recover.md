---
title: "Partition DELETED! Cannot recover"
date: 2009-06-27
forum: General Help
---

### Post by asusx on 2009-06-27
:cry:
Here is what happened. I've accidentally formatted my ubuntu ext4 partition to hfs+. I've tried Testdisk to recover the files in partition, but I get "filesystem seems damaged" error. I've tried photorec, but the files are not recovered the same way(ie. folders are cleated randomly and file names are not the same)
So is there a way I can copy the files from the ext4 partition with the same structure and file names?

---

### Post by Dysport on 2009-06-27
> **asusx said:**
> :cry:
So is there a way I can copy the files from the ext4 partition with the same structure and file names?

Formatting deletes the partition table, thus the filenames and folder structures.
But as you mentioned Photorec still finds data. This is not random data, it's your actual lost data. But of course it will take a lot of time browsing through it and recover the important stuff.
I had to do this once, too - went well for me with Photorec. Alternatively you could also try sleuthkit/autopsy.

---

### Post by asusx on 2009-06-27
Thnx for reply.. 
I wonder if there is a way to select what to recover and what not. Is there a way i can do this?

---

### Post by Dysport on 2009-06-27
I think in photorec you can specify which file types you want to recover (.jpg, .doc, …) somewhere in the menu before the actual start of the recovery process.

---

### Post by asusx on 2009-06-27
ok, I'll try that.
Also, if i recover the ext4 with testdisk, will the files be there?

---

### Post by Dysport on 2009-06-27
I've never worked with Testdisk. Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=387922") will help.
Good luck!

---

### Post by cmost on 2009-06-27
Sorry about the loss of your partition.  You probably don't want to hear this now but I think it's prudent to stress the importance of backing up important files and folders BEFORE mucking around with your filesystem.  External hard disks are dirt cheap these days and with easy to use file synchronization tools like Grsync, backing up on a regular basis is a snap.  Good luck recovering your data!  :P

---

### Post by unutbu on 2009-06-27
Jaunty's testdisk package is version 6.10. 
Only TestDisk version 6.11 (or later) can read ext4.

So if you haven't tried TestDisk version 6.11, perhaps you should try it again. 

You can get the latest version here:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

To download and run TestDisk version 6.11.3, open a terminal (Applications>Accessories>Terminal) and run the following commands:
```
wget [http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2)
tar xvjf testdisk-6.11.3.linux26.tar.bz2
sudo testdisk-6.11.3/linux/testdisk_static
```

Because you have reformated the partition, I'm not certain you'll be able to recover the original ext4 filesystem completely, but I have seen blogs and posts of people who say they've managed to recover nearly everything by using testdisk.

Good luck.

---

