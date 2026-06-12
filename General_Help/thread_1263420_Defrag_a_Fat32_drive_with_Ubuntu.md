---
title: "Defrag a Fat32 drive with Ubuntu"
date: 2009-09-11
forum: General Help
---

### Post by sleepitoff on 2009-09-11
Hello, I have an external drive that's in Fat32 format and I'm wondering if there's a way to defrag this drive using Ubuntu.

---

### Post by ankspo71 on 2009-09-11
Hi,
Is your external drive for a windows installation or for storage? Either way, you might be able to find a freeware defragmentor that runs under WINE to defragment that other drive. I wouldn't invest in a commercial defragmentor unless it was said to work in linux/wine though.

I was a dual hard drive windows user for several years, and I never noticed any large fragmentation on my storage drive. There were small fragments on occasion, but not much. From what I have read... most fragmentation is caused by having a page file on the same partition as the OS (eg: MS Windows). Now that I am a linux user for about 1.5 years I haven't thought about fragments in my storage drive much, because I haven't seen my storage drive performance get worse. I did defragment it anyways, when I was using windows though.
James

---

### Post by lensman3 on 2009-09-11
Take a look of the programs called "mtools".  It knows about fat(s).  They might do what you want.

The other way is do a "tar" (backup) on the entire drive and save everything to another drive.  Delete all files on the vfat drive.  Then restore the files back to the vfat drive.  (This is how VAX VMS systems were defrag'ed back in the '80's).  The "tar" as is collects the files will put them in file/disk sequential order).  When you write the files back, everything is then defraged.

Hope this helps.

---

### Post by sleepitoff on 2009-09-11
This drive is purely for storage and space is running low on it, so I was thinking that since it's a Fat32 drive it may need to be defragmented. 

I would simply reformat the drive to ext3, but I can't loose the data that's on the drive and have no other storage unit to transfer the data over to while I reformat it. 

But I will look into mtools and also on the wine site for working software. Thank you.

---

### Post by akakingess on 2009-09-11
> **lensman3 said:**
> Take a look of the programs called "mtools".  It knows about fat(s).  They might do what you want.

The other way is do a "tar" (backup) on the entire drive and save everything to another drive.  Delete all files on the vfat drive.  Then restore the files back to the vfat drive.  (This is how VAX VMS systems were defrag'ed back in the '80's).  The "tar" as is collects the files will put them in file/disk sequential order).  When you write the files back, everything is then defraged.

Hope this helps.

Thank you for this information, I may actually use this as a backup and defrag at the same time, very convenient. That's why I love the people willing to share cool tips like this in the Ubuntu community.

---

