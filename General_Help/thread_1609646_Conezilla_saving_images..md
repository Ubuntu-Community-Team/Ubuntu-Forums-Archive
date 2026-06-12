---
title: "Conezilla: saving images."
date: 2010-10-30
forum: General Help
---

### Post by wilee-nilee on 2010-10-30
So up to lately I had never messed with imaging hard drives or partitions.

I understand clonezilla basically, except a back up from a HD that has ntfs and ext linux type partitioning. Do I save these separately as allowed in clonezilla?

I did a backup of the 160gig hd (W7,Maverick) just as a test to an external that was ntfs. It looked okay, I think this is okay, I'm just trying to confirm the partition type of the save HD, that may be suggested in general. 

I followed these pretty good instructions to get the general idea of clonezilla and using it.
[http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla](http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla)

---

### Post by CharlesA on 2010-10-30
The file system of the drive storing the images doesn't really matter. (except FAT32, but the images are split into 2GB chunks)

I've saved images to NTFS, EXT3 and EXT4 without any problems.

Did you have any other questions about it?

---

### Post by wilee-nilee on 2010-10-30
> **CharlesA said:**
> The file system of the drive storing the images doesn't really matter. (except FAT32, but the images are split into 2GB chunks)

I've saved images to NTFS, EXT3 and EXT4 without any problems.

Did you have any other questions about it?

I suspected that this was the case as I had looked at the files, and no red flags anywhere really about this.

Thanks I appreciate the help, I will have to when I have time due a actual full image and restore to know more.

---

### Post by CharlesA on 2010-10-30
No problem. 

A full image would look something like this:

```
charles@thor:~$ ls -l /array/clone/Osiris_Vista_SP2_8-16-2010/
total 11742892
-rw-rw---- 1 clone clone          4 2010-08-16 22:05 disk
-rw-rw---- 1 clone clone      13295 2010-08-16 22:05 Info-dmi.txt
-rw-rw---- 1 clone clone      15409 2010-08-16 22:05 Info-lshw.txt
-rw-rw---- 1 clone clone       1882 2010-08-16 22:05 Info-lspci.txt
-rw-rw---- 1 clone clone        260 2010-08-16 22:05 Info-packages.txt
-rw-rw---- 1 clone clone          5 2010-08-16 22:05 parts
-rw-rw---- 1 clone clone 2097152000 2010-08-16 21:51 sda1.ntfs-ptcl-img.gz.aa
-rw-rw---- 1 clone clone 2097152000 2010-08-16 21:53 sda1.ntfs-ptcl-img.gz.ab
-rw-rw---- 1 clone clone 2097152000 2010-08-16 21:57 sda1.ntfs-ptcl-img.gz.ac
-rw-rw---- 1 clone clone 2097152000 2010-08-16 22:00 sda1.ntfs-ptcl-img.gz.ad
-rw-rw---- 1 clone clone 2097152000 2010-08-16 22:02 sda1.ntfs-ptcl-img.gz.ae
-rw-rw---- 1 clone clone 1537819383 2010-08-16 22:05 sda1.ntfs-ptcl-img.gz.af
-rw-rw---- 1 clone clone         37 2010-08-16 21:48 sda-chs.sf
-rw-rw---- 1 clone clone    1048064 2010-08-16 21:48 sda-hidden-data-after-mbr
-rw-rw---- 1 clone clone        512 2010-08-16 21:48 sda-mbr
-rw-rw---- 1 clone clone        261 2010-08-16 21:48 sda-pt.parted
-rw-rw---- 1 clone clone        259 2010-08-16 21:48 sda-pt.sf

```

I've gotten into the habit of restoring the image immediately after creating it just to make sure it's a good image.

You can also check the integrity by using this:

```
cat sda1* | gzip -tv -
```

---

### Post by wilee-nilee on 2010-10-30
That is good information.

I have always just had hard copies and or iso's of the OS and just backed up the needed media.

I actually did a restore of W7 yesterday as I had gotten a little aggressive I think with some comodo tools and removed the drivers or the registry stuff that made my W7 unable to reach the net.

Granted I hardly ever use it except to help MS users, but the restore was easy and fast, I didn't do a complete re-image I have that saved, although I think that is what it did automatically from the booted W7 ISO on a thumb. I got the W7 ISO from Digital River when I bought the upgrade to W7. The regular download from them was not the ISO, I knew better I got both, and a DVD copy. They sent me two DVD's for the price of one so I have a shiny coaster.

It is more efficient to have these images rather then a fresh install at times just for time saving at the least. I don't really tweak my setup too custom so I can be up and running as usual with a fresh install, within less then a hour after installing and updating the OS.

It helps to know this stuff as well to share on the forum.

---

