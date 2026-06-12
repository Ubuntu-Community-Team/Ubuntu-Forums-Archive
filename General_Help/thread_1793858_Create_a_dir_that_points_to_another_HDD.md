---
title: "Create a dir that points to another HDD"
date: 2011-06-30
forum: General Help
---

### Post by XCan on 2011-06-30
I am currently running a lot of simulations and am always interested to speed things up a bit. My workstation has 2 hdds, 1 ssd-drive (sda1) and 1 mechanical platter drive (sdb1). Of course, most of my data are on the mechanical drive and the ssd is mostly used for booting. 

However, to speed things up a bit, I wonder if it is possible to create a pointer or link in a directory residing within the mechanical drive, which will write the data, in reality, to the ssd instead. For example, 
```
 /home/me/sims/data/dump
```
would normally reside on sdb1. But I would like it to point to a mount point of the ssd instead, e.g.,
```
 /ssdtemp/dump
```

---

### Post by dcstar on 2011-06-30
> **XCan said:**
> I am currently running a lot of simulations and am always interested to speed things up a bit. My workstation has 2 hdds, 1 ssd-drive (sda1) and 1 mechanical platter drive (sdb1). Of course, most of my data are on the mechanical drive and the ssd is mostly used for booting. 

However, to speed things up a bit, I wonder if it is possible to create a pointer or link in a directory residing within the mechanical drive, which will write the data, in reality, to the ssd instead. For example, 
```
 /home/me/sims/data/dump
```
would normally reside on sdb1. But I would like it to point to a mount point of the ssd instead, e.g.,
```
 /ssdtemp/dump
```

```
man ln
```

---

### Post by ajgreeny on 2011-06-30
First make sure all the partitions on the disks are mounted at boot time by /etc/fstab or you will end up with broken links.  Now using nautilus go to the folder where the files really sit, and with the middle mouse button, click and drag the folder to where you want the link to be.  When you release the middle button a small dialog will appear asking if you want to move, copy or link here.  Obviously choose "Link".

Simple!  All the files you put into the link folder will actually be in the other one.

---

### Post by tredegar on 2011-06-30
This is what I think you need to do:

You need to create a partition on sda (your SSD) large enough to hold your data.
Format that partition, perhaps as ext3
Mount it at **/mnt/dump**
Copy your data to it
Unmmount it
Re-mount it at **/home/me/sims/data/dump**

Now all the files below **/home/me/sims/data/dump/** are on your SSD even if **/home** is on your mechanical drive.

Alternatively, copy all your data to a directory on your SSD. Then delete /home/me/sims/data/dump
Then make a link called /home/me/sims/data/dump that points to the directory on your SSD where the data really is.

---

