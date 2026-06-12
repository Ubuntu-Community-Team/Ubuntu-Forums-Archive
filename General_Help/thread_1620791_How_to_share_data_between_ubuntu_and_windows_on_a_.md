---
title: "How to share data between ubuntu and windows on a dual boot system?"
date: 2010-11-13
forum: General Help
---

### Post by Blue Dolphins on 2010-11-13
My harddrive died and I just replaced it and I still haven't reinstalled any OS's yet.  I want to be able to share all my media files between Xubuntu 10.4 and Windows XP.  I have read up a bit on it and I think the way I want to do it is to create a FAT32 partition and keep all the media I want to share between OS's on that partition, as from what I read FAT32 is much more linux compatible than NTFS.

Would there be any significant decrease in performance in linux over having the data stored on an ext partition? I have over a 100Gb of music, would loading the library when I launch the music player take alot longer, would there be lag playing movies or songs?  How would I configure Xubuntu so that the FAT32 partition is automatically mounted at startup?

---

### Post by zvacet on 2010-11-13
I don´t think you will have problem if you format one partition as NTSF,because Ubuntu can read & write on it.Since you didn´t reinstall any OS then install Windows first.You can make your data partition when you install Windows.After that install Ubuntu and format it as ext4 ( yopu can make separate home if you want).Ubuntu will recognize your WIn partitions and you will be able to put your media stuff on data partitions and both OS will be able to read it.

---

### Post by coffeecat on 2010-11-13
> **Blue Dolphins said:**
> as from what I read FAT32 is much more linux compatible than NTFS.

Then what you've been reading has been very much out-of-date. NTFS read-write support has been reliable in Ubuntu for at least two years. I use shared NTFS data partitions on my two laptops and used to use one on my desktop when it had Windows. I've never had a problem. NTFS is more robust than FAT32 and doesn't have FAT32's 4GB filesize limit.

> **Blue Dolphins said:**
> How would I configure Xubuntu so that the FAT32 partition is automatically mounted at startup?

For FAT32 or NTFS you need to edit /etc/fstab to mount your partition on bootup. If you want to do this yourself, this is a good link:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Alternatively, there is an app in the repos called ntfs-config. I don't like it because it sometimes does strange things, and don't let it set up an automount for your Windows C: partition, which it will if given half a chance. That is not a good idea.

---

### Post by pratzy on 2010-12-30
Very simple fix...install a utility 'Gigolo'. Its a frontend to view remote filesystems

---

