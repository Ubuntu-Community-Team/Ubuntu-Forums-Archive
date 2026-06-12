---
title: "Converting to FAT32 and mounting in Ubuntu"
date: 2011-02-20
forum: General Help
---

### Post by frogknowledge on 2011-02-20
Okay days of searching and no luck.

I have a 500GB Hard Drive NTFS format that is full of movies and pictures. I want to convert it to FAT32 and connect to XBOX 360. 

I have GMount and have been doing test with a smaller 4GB flash drive. The drive was NTFS I was able to format it to a FAT32 no problem. Was not able to mount it in ubuntu so that I could actually add files to it . Ubuntu knows that the 4GB is their but will not let me open or mount it.

So can you change a hard drive to a FAT32 and still write to it from in Ubuntu if so how?

---

### Post by coffeecat on 2011-02-20
> **frogknowledge said:**
> So can you change a hard drive to a FAT32 and still write to it from in Ubuntu if so how?

Ubuntu has been able to write to FAT32 longer than to NTFS

> **frogknowledge said:**
> I have GMount and have been doing test with a smaller 4GB flash drive. The drive was NTFS I was able to format it to a FAT32 no problem. Was not able to mount it in ubuntu so that I could actually add files to it . Ubuntu knows that the 4GB is their but will not let me open or mount it.

GMount? What is that? Ubuntu will automount both NTFS and FAT32 formatted drives as soon as they are plugged in. You don't need anything else. If Ubuntu was not able to mount the flash drive, then there might be something wrong either with the FAT32 filesystem or the drive itself.

---

### Post by jerenept on 2011-02-20
> **frogknowledge said:**
> Okay days of searching and no luck.

I have a 500GB Hard Drive NTFS format that is full of movies and pictures. I want to convert it to FAT32 and connect to XBOX 360. 

I have GMount and have been doing test with a smaller 4GB flash drive. The drive was NTFS I was able to format it to a FAT32 no problem. Was not able to mount it in ubuntu so that I could actually add files to it . Ubuntu knows that the 4GB is their but will not let me open or mount it.

So can you change a hard drive to a FAT32 and still write to it from in Ubuntu if so how?

I don't think FAT32 supports such large hard disks anyway.

---

### Post by frogknowledge on 2011-02-20
> **coffeecat said:**
> 

GMount? What is that? 

Sorry GParted

---

### Post by tredegar on 2011-02-20
I don't think you can change a filesystem "on the fly".

I think you will have to copy your files somewhere else, double-check that they are really there, then reformat the original drive.

Then copy the files back.

FAT32 has a maximum *file* size of 4GB. The maximum *partition* size seems to be 2TB, so your disk should be OK as FAT32 if you do not have any individual files > 4GB

---

### Post by HermanAB on 2011-02-20
It doesn't sound like you formatted the drive yet, just messed with the partitioning, which wasn't necessary.

You can easily partition a disk with fdisk (or gparted), then format it with mkfs:
$ sudo mkfs.vfat /dev/sdx1

---

### Post by jalanbuntu on 2011-02-20
> **jerenept said:**
> I don't think FAT32 supports such large hard disks anyway.

No problem with the 500GB large size, the only problem is that you can't have **a file** which size larger than **4G** on FAT32 filesystem. Use gparted or the fdisk alternative: gdisk.  I've been use it since ice age n no problem so far :lol:

---

