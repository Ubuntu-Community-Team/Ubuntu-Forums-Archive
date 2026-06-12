---
title: "fat32 vs ntfs"
date: 2010-05-30
forum: General Help
---

### Post by COKEDUDE on 2010-05-30
> Ntfs - the only filesystem allowing read/write access and files greater than 2GB under Windows and Linux. Good for USB storage.

Read more: [http://wiki.linuxquestions.org/wiki/Interoperability#ixzz0pT2WwELY](http://wiki.linuxquestions.org/wiki/Interoperability#ixzz0pT2WwELY)

[http://wiki.linuxquestions.org/wiki/Interoperability](http://wiki.linuxquestions.org/wiki/Interoperability)

Is this no longer accurate about fat32? I just used a 4 gb flash drive to share several video files between Windows XP and Linux Mint. 

I also plan on sharing several files in the future with that 4 gb flash drive between XP and Mint so I was wondering if I should use fat32 or ntfs. Fat32 seems faster than ntfs, so I think I would prefer fat32. Please explain why with whichever way you say.

---

### Post by Sef on 2010-05-30
NTFS is better to use because among other things, it is more stable than FAT32.

---

### Post by BoneKracker on 2010-05-30
I think that (2 GiB) was the upper limit of a FAT16 filesystem on Windows machines.

---

### Post by COKEDUDE on 2010-05-30
What about that 2 gb restriction? Does it no longer exist?

---

### Post by BoneKracker on 2010-05-30
> **COKEDUDE said:**
> What about that 2 gb restriction? Does it no longer exist?

As I understand it, on FAT16 the 2 GiB limit does still exist.  On FAT32, it does not.

As I recall, FAT32 to can to 4 Terabytes or something like that.  You could look it up on the Microsoft web site.

In terms of performance, [these tests]("http://www.testfreaks.com/blog/information/usb-flash-drive-comparison-part-2-fat32-vs-ntfs-vs-exfat/") indicate that FAT32 will probably outperform NTFS marginally on a 4 GiB flash drive.

However, as I recall FAT is more vulnerable to fragmentation than NTFS.  So if the drive is likely to be pretty full and not being emptied (like you're carrying a lot of crap around on it, in addition to using it for occasional file transfer), then I myself would probably go with NTFS.  But I am no expert on this.

---

### Post by bakegoodz on 2010-05-30
fat32 has filesize limit of 2 GB for a single file

---

### Post by BoneKracker on 2010-05-31
> **bakegoodz said:**
> fat32 has filesize limit of 2 GB for a single file

I believe FAT32's maximum _file_ size is 4 GiB (actually, it's 4 GiB minus 1 byte).

FAT_16_ has a filesize limit of 2 GiB (unless you use cluster sizes inappropriately large for most purposes, in which case you can go as large as 4 GiB).

---

### Post by oldfred on 2010-05-31
NTFS has journalizing so data recovery is possible, but that takes space (and I assume time). 

I would only use FAT on files I do not care about (e,g, almost never), but some devices like camera flash cards have to use it.

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by formaldehyde_spoon on 2010-05-31
> **bakegoodz said:**
> fat32 has filesize limit of 2 GB for a single file

This is not correct. 
I think the OP is getting confused between file size, and partition size.

FAT16 had a max file size of 2 GB, AND, a max partition size of 2 GB.
FAT32 has a max file size of 4 GB, and a max partition size of 8 TB.

The ''4 GB'' flash drive is the partition size.
Seeing as you can't possibly have a file size greater than 4 GB (because your partition is only 4 GB) you will never notice any size limits of any sort by using FAT32 on that flash drive.  

For the record NTFS max file size is 16 EB, and it's max partition size is also 16 EB. 

EDIT: some links above say NTFS's maxes are 2TB and 2TB, and FAT32 max partition is 2TB, so I guess I am wrong about that.  The 2 TB sounds much more believable to me.

---

### Post by BoneKracker on 2010-05-31
> **formaldehyde_spoon said:**
> This is not correct. 
I think the OP is getting confused between file size, and partition size.

FAT16 had a max file size of 2 GB, AND, a max partition size of 2 GB.
FAT32 has a max file size of 4 GB, and a max partition size of 8 TB.

The ''4 GB'' flash drive is the partition size.
Seeing as you can't possibly have a file size greater than 4 GB (because your partition is only 4 GB) you will never notice any size limits of any sort by using FAT32 on that flash drive.

For the record NTFS max file size is 16 EB, and it's max partition size is also 16 EB.
++ that tracks with my understanding

---

### Post by oldfred on 2010-05-31
While not directly related to NTFS or FAT the 2TB limit may be because under MBR partitioning 2TB is the max. NTFS can be on other partitioning schemes so larger sizes can be used but not under MBR.

---

### Post by formaldehyde_spoon on 2010-05-31
> **oldfred said:**
> While not directly related to NTFS or FAT the 2TB limit may be because under MBR partitioning 2TB is the max. NTFS can be on other partitioning schemes so larger sizes can be used but not under MBR.

Cheers for that Fred, I was wondering...

---

### Post by COKEDUDE on 2010-06-03
Thx everyone for sharing all of this information. It was very helpful and informative.

---

