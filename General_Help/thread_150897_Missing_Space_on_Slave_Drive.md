---
title: "Missing Space on Slave Drive"
date: 2006-03-26
forum: General Help
---

### Post by fishmorg909 on 2006-03-26
Okay, I got a Maxtor 40GB HDD set up as slave drive to existing Ubuntu drive. It had Win XP on it, but it crapped out on me, and using fdisk I set it up as one big storage drive, no partitions. I got it mounted in Administration>Disks, but there's an odd shortage. It's a 40GB drive, but Disks and Glparted tell me there's 37GB available... there is nothing on there but an empty "lost & found" folder. How do I find out if it's corrupt, or needing optimization? (Or whatever.)

P.S. At no time during the reformatting did a corruption-detected message show up.

---

### Post by nanotube on 2006-03-26
this is normal - all drive manufacturers tell you the disk is "40 gb" but it is actually only 37. the reason this is is that they take the number of bytes and divide it by 1,000,000,000 to get their gigabytage, while the actual gigabyte is 1024^3 = 1,073,741,824 bytes. if you take 40,000,000,000 and divide it by the actual size of a gigabyte, you will get 37. so, there is no problem, just a marketing gimmick. :)

---

### Post by fishmorg909 on 2006-03-27
Wait a minute --  did I misread it before? Disk manager actually says that I have  **34.7GB** available on the empty slave drive. That can't be right! I repeat my above question... 5.3 missing GBs is awfully high. :confused: 

And how can I get the slave drive to automount on startup? Diskmounter just tells me that there are no usable Mac or Win setups on the disk. and does not mount it, even though it's all set for (and works fine in) Ubuntu.

---

### Post by fishmorg909 on 2006-03-27
Looking around on the forums, I learned I could mount slave drive with permissions just by:
```
sudo gedit /etc/fstab
```
and adding to bottom of lines:
```
/dev/hdb1 /media/drive2 ext3 defaults 0 0
```
and adding a directory:
```
sudo mkdir /media/drive2
```

So now it boots up fine, with full permissions. Still wonder about missing drive space -- Disk Mounter still says I have 34.7GB on the empty drive -- and Glparted says I have 38.16GB! Huh? That's quite a difference... :confused:

---

### Post by megamania on 2006-03-27
[QUOTE=fishmorg909] Still wonder about missing drive space -- Disk Mounter still says I have 34.7GB on the empty drive -- and Glparted says I have 38.16GB! Huh? That's quite a difference... :confused:[/QUOTE]

It might be do to the fact that ext2/3 systems reserve a percentage (usually5%) of the disk for use by root.

```
sudo tune2fs -m 0 /dev/hda (change to the appropriate device name)
```
is supposed to fix it, and you will get the missing space back. 

Anyway, keep in mind that it should be used  on an unmounted hd only.

Hope that's what you were looking for.

EDIT: as far as I know, you are encouraged to leave the reserved space on the drive (I removed it because I needed those "missing" 10 Gb!)

---

### Post by fishmorg909 on 2006-03-27
Just checked again, and both Glparted and Disk Manager agree that there's some 38GB on there. Guess I'll leave it for now -- thanks.

---

