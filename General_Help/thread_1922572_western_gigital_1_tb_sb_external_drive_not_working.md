---
title: "western gigital 1 tb sb external drive not working ubuntu 11.1"
date: 2012-02-09
forum: General Help
---

### Post by peterkp on 2012-02-09
Sir,
My 1TB external hard disk works fine in windows. when I connect it to ubuntu it mounts and show a cd drive with 450 MB. with some windows files .These file in windows (exe) is used to unlock and connect then i can see data. In ubuntu as this files are exe, I am unable to run and the data is not visible. Please help me.

---

### Post by sikander3786 on 2012-02-09
Probably your HDD is formatted "Dynamic Disk" in Windows 7. That is a Microsoft proprietary thing and doesn't work with Linux. Just to make sure, press the <Super> (Windows logo) key and search for and start the "Terminal" and then post the output of this command:

```
sudo fdisk -lu
```

---

### Post by dcstar on 2012-02-09
> **sikander3786 said:**
> Probably your HDD is formatted "Dynamic Disk" in Windows 7. That is a Microsoft proprietary thing and doesn't work with Linux. Just to make sure, press the <Super> (Windows logo) key and search for and start the "Terminal" and then post the output of this command:

```
sudo fdisk -lu
```

Yep, useless Windows software installed on the drive with the arrogant assumption that "only" Windows users need to use this drive.

Take any data off it, use **gparted** to write a new Partition Table (which will totally wipe it) and then use the drive like any other storage device.

---

### Post by Mark Phelps on 2012-02-09
Did you buy the drive pre-formatted (like WD does)?  Then likely, the drive supplier loaded it with some Windows SW -- presumably to allow you to easily "manage" the filesystem, which (as dcstart has pointed out) renders it inaccessible in Linux.

Reformatting (to remove the Windows SW) is going to be the only way to get access to it.

---

### Post by xyzzyman on 2012-02-09
Just hook it up to a windows system, and do a permanent unlock with the software. Then it'll work fine in linux, and you still have the option to use as mfg'd later.

You may want to look at TrueCrypt for a cross-platform solution for locking down the drive. There is even a portable windows version you can leave on the HDD itself.

---

