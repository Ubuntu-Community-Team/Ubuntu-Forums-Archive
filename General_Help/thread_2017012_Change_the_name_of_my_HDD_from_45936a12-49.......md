---
title: "Change the name of my HDD from 45936a12-49......"
date: 2012-07-04
forum: General Help
---

### Post by cforput on 2012-07-04
I have a bunch of partitions on my HDD. I have a really big one for all my data then other partitions for different OS's (Ubuntu, Mint, windows). My "data" partition is listed in /media as 45936a12-2cd9-ad5a-9a47-bad15969dbd. I want to change this to something like "Data" or "Common_Data". Something simple and easy to type. How do I do that?

I'm a newbie so please give as many details as possible. I saw something about using Disk Utility but when I go into it, I see where I can label my different partitions but I'm not sure that is what I want to do. If I change the label, will it affect programs that are looking for data on the 459.... label?

Any help would be much appreciated.

---

### Post by msammels on 2012-07-04
No, it will not. The label is just that - a label. Programs tend to search /dev/sda. You can't change that. Feel free to label to your heart's content! :D

---

### Post by cforput on 2012-07-04
Thanks but I don't know how to relabel it. What program / process would I use?

---

### Post by oldfred on 2012-07-04
You can use Disk Utility, gparted or the command line. If I remember I do it when I create the partition with gparted. Otherwise I usually use Disk Utility. FAT partitions are all capitals (still I think).

Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)


Then you can see your labels like this:

f```
red@fred-Precise:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    /mnt/cdrive    04B05B70B05B6768
/dev/sda2  ext3    backup   /media/backup  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdc8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdc9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdc10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdc11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdc12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdc13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdc14 ext4    kubuntu  (not mounted)  2b42c9ad-4304-4a8a-8991-08cfe35717ec
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdc17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdc18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    quantal  /media/quantal 3b72e3d4-3d56-469b-ad50-f13ac4f5f0d4
```

You can also use labels to automatically mount partitions in fstab.

---

