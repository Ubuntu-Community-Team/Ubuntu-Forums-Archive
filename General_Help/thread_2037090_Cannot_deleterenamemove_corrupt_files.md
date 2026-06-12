---
title: "Cannot delete/rename/move corrupt files"
date: 2012-08-03
forum: General Help
---

### Post by gettheinfoandgo on 2012-08-03
Hi, 

I recently downloaded a few audio and video files onto my laptop, moved a few others from a friend's iphone, then moved them all onto my external hard drive.  Some of them were scrambled in the process: I open an .avi file and it plays a different .mp4 file.  I tried to delete the corrupt files and it says "no such file or directory."

They cannot be moved, either.  I've tried rm -f and in a sudo nautilus window to no avail.  I also cannot replace them with the intact version of the files, which i still have on my laptop.

Any thoughts?  I would LOVE to get these gone!  I can't even rename them to make them invisible.

Thanks in advance.

---

### Post by idoitprone on 2012-08-03
> **gettheinfoandgo said:**
> Hi, 

I recently downloaded a few audio and video files onto my laptop, moved a few others from a friend's iphone, then moved them all onto my external hard drive.  Some of them were scrambled in the process: I open an .avi file and it plays a different .mp4 file.  I tried to delete the corrupt files and it says "no such file or directory."

They cannot be moved, either.  I've tried rm -f and in a sudo nautilus window to no avail.  I also cannot replace them with the intact version of the files, which i still have on my laptop.

Any thoughts?  I would LOVE to get these gone!  I can't even rename them to make them invisible.

Thanks in advance.

```
blkid
```

it depends if your external harddrive ntfs or linux filesystem

If it is ntfs, then get a windows computer and rune

```
chdsk [driveLetter]
```
ex.
```
chdisk d:
```

if it is linux filesystem


```
fdisk [path to drive partition]
```


ex.
```
fdisk /dev/sdb1
```

---

### Post by TheFu on 2012-08-03
> **gettheinfoandgo said:**
> Hi, 

I recently downloaded a few audio and video files onto my laptop, moved a few others from a friend's iphone, then moved them all onto my external hard drive.  Some of them were scrambled in the process: I open an .avi file and it plays a different .mp4 file.  I tried to delete the corrupt files and it says "no such file or directory."


Could it be that the filenames have non-standard characters?  Have you tried using regex pattern matching to remove the files from a terminal?  I've seen some files have \r\n embedded in the names which caused GUI tools all sorts of issues.

The other idea about running fsck is a good one too.  If the partition is NTFS, there is a Linux tool for that .... need to look it up ... called **ntfsfix** and **fsck.vfat**.  Never tried them, but others have had good success, I've heard.

---

### Post by gettheinfoandgo on 2012-08-03
thank you - will post back after a few attempts.

---

### Post by idoitprone on 2012-08-05
> **TheFu said:**
> Could it be that the filenames have non-standard characters?  Have you tried using regex pattern matching to remove the files from a terminal?  I've seen some files have \r\n embedded in the names which caused GUI tools all sorts of issues.

The other idea about running fsck is a good one too.  If the partition is NTFS, there is a Linux tool for that .... need to look it up ... called **ntfsfix** and **fsck.vfat**.  Never tried them, but others have had good success, I've heard.

dont use linux tools to fix ntfs.

ntfs went through a few revisions over the years.

Use windows chkdisk

---

