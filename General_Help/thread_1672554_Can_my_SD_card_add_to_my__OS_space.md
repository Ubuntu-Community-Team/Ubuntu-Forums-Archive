---
title: "Can my SD card add to my / OS space?"
date: 2011-01-21
forum: General Help
---

### Post by kittkatt on 2011-01-21
I have an eeepc701SD with 4gigs of internal space.  After the install of lubuntu + all the programs I need, I have under 1 gig left of room.  I also have a 4g SD card mounted under /media/SDCard . 

I have learned that due to the way the repository system works, I can't choose to install my programs on my SD card.  I was wondering if there was any way to use my SD card to increase the "root" space on my 4g netbook?

---

### Post by tredegar on 2011-01-21
I also have an EEE701. Ubuntu 10.04 is on the internal 4GB, so there was little (no) room for anything else.
So I formatted a 16GB SD card as 2 partitions with ext3, one 4GB partition, one 12GB partition

Then I booted linux from a live usb and mounted /dev/sda1 at /mnt/sda1 
I mounted my SD card partitions at /mnt/card1 and mnt/card2

I copied all of /usr from /mnt/sda1 to the 4GB partition.
I copied all of /home from /mnt/sda1 to the 16GB partition
I deleted all the files from /usr (but left the directory) on /dev/sda1
I deleted all the files from /home (but left the directory) on /dev/sda1
I fixed up /etc/fstab to mount the 4GB partition as /usr using UUID= for the UUID of that partition
I fixed up /etc/fstab to mount the 12GB partition as /home using UUID= for the UUID of that partition
Eg 
```
UUID=04450b5a-a6ef-479d-98b5-cbfc4667861b /usr  ext3 defaults 0 2
UUID=22cdc46f-a6e4-43c6-ac42-9046e5fc5372 /home ext3 defaults 0 2

```
(You can list the UUIDs of your partitions with the **blkid** command.)

I shutdown, removed the live USB stick and rebooted. Now there is plenty of space for "everything" because /home and /usr are on the SD Card.

That EEE is a neat little computer.

---

