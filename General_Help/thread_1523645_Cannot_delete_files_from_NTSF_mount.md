---
title: "Cannot delete files from NTSF mount"
date: 2010-07-04
forum: General Help
---

### Post by savaan on 2010-07-04
I've got a 250gig removable drive mounted on my Lucid 10.04. I'm having a problem deleting files. It starts by saying "Cannot move  file to trash. Do you want to delete immediately". So I click Delete. Then I get "Error removing file: Input/output error"...and my files stay. 
This is the last grasp Windows has on my household :/ This is on my media machine and I'm converting it this weekend...but I'm trying to backup some stuff on this drive which is still on the old Windows partitioning and formatting. I just need to delete some larger files to make room for my new backups

---

### Post by savaan on 2010-07-05
no one ? :( bump?

---

### Post by Serpher on 2010-07-05
If you're deleting them just go to System --> Administration --> gParted (Or Disc management it's called in some versions), and delete the NTFS partition after executing this command in a terminal:

```
sudo umount /media/*
```

---

### Post by Directive 4 on 2010-07-05
i've had this same problem on a number of drives,  ntfs and ext4
the dreaded input/output error, 

first time it happened it started spreading to more and more files, problems with moving, copying, deleting.

i solved it by copying everything to another hard drive, reformatin the problem drive (gparted) and copying the files back,

this was after a few days of working on the problem with no success

if you have or can borrow another drive i'd rec this as it's easy? and at least you know it's going to work.

maybe I/O errors means the hard drive has problems but for me these problems went away with this method
 both hard drives are working great now.

good luck!:D

---

### Post by savaan on 2010-07-05
> **Serpher said:**
> If you're deleting them just go to System --> Administration --> gParted (Or Disc management it's called in some versions), and delete the NTFS partition after executing this command in a terminal:

```
sudo umount /media/*
```

I don't want to delete the partition. I'm trying to delete files on this removable drive to make room for more backup files

---

### Post by btindie on 2010-07-05
Can you create new files on the partition? If not then it may simply be a permissions problem. Try remounting it with full write access for all users
```
sudo mount -o remount,umask=0 /dev/sdX
```
where sdX is your NTFS partition.

---

### Post by savaan on 2010-07-05
my drive is located at ```
sudo mount -o remount,umask=0 /media/FreeAgent Drive/
```
but when i run that in terminal i get ```
mount: you must specify the filesystem type
```

---

### Post by btindie on 2010-07-05
If your path has got a space in it then you need to escape it
```
sudo mount -o remount,umask=0 /media/FreeAgent\ Drive
```

---

