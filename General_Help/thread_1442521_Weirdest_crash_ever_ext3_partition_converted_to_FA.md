---
title: "Weirdest crash ever: ext3 partition converted to FAT32"
date: 2010-03-30
forum: General Help
---

### Post by db0 on 2010-03-30
Hello all, I just wanted to post this issue to see if anyone has ever seen anything like this or knows an easy way to revert it.

I have a media/file Ubuntu server. On it I have various external USB HDDs attached which serve as the main storage area. At the moment I have two of 1 TB each. One was formatted at ext3 and the other as NTFS. 

Yesterday night I was working on my Ubuntu media server via ssh. I was rsyncing the music collection we have in common with my girlfriend from one external disk to the other. However, my girlfriend is used to shutting down the PCs before going to sleep and even though I told her she does not need to shut down the server, she went ahead and did it out of habit (via the xbmc interface).

This meant that my rsync session closed abruptly and I was kicked out. So I say "ok, no prob, lets just restart the server". Well I do that and I notice that my ext3 HDD is not mounting (it's on fstab with uuid). I try to mount it manually: No go. It gives me an error (don't have it with me atm, something about back block iirc). I do an fdisk -l and to my great surprise I notice that it now lists the HDD filesystem as FAT32!

At this point I started panicking as I was sure everything has been wiped. I do an fsck and let it run all night. I then go back and check. Still FAT32!

a simple "mount /media/store1" fails with the previous error. However when I tried a "mount -t auto /dev/sdb1 /media/store1" it mounted. And not only that, but I can see the contents as well and they also seem to be in working order!

This is some weird stuff right here. Has anyone ever seen anything like this? Is there some way I can restore my partition to its previous ext3 goodness without formatting it? I just for the life of me can't imagine how this happened and doing a google search doesn't provide me with any relevant stuff.

---

### Post by lotharmat on 2010-03-30
Has the rsync gone 'the wrong way'?

---

### Post by db0 on 2010-03-30
No, not at all.

---

### Post by Fafler on 2010-03-30
With the ext3 filesystem intact, you just need to change the filesystem type in the partition table.
```
sudo fdisk /dev/sdb
t
1
83
w
```

---

### Post by Sef on 2010-03-30
> s there some way I can restore my partition to its previous ext3  goodness without formatting it? I

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Download"), so you can (hopefully) recover  your partition.

---

### Post by Grenage on 2010-03-30
It's obviously not been converted to FAT32, but it's possible that the partition table has in some way been corrupted.

I haven't had any experience with tools that check and repair partition information (I'm deranged, and would usually just delete and create it via fdisk).

---

### Post by db0 on 2010-03-30
Thanks for all the advice people. I'll try to first just swap the filesystem type with fdisk and see if it works, otherwise I'll check out this Test_Disk.

---

### Post by lotharmat on 2010-03-30
Let us know how you get on!

---

### Post by db0 on 2010-03-31
> **Fafler said:**
> With the ext3 filesystem intact, you just need to change the filesystem type in the partition table.
```
sudo fdisk /dev/sdb
t
1
83
w
```

This solution worked perfectly (although I didn't have to press 1 as it's the only FS on the disk). Thank you muchly!

---

