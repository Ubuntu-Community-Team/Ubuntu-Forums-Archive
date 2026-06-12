---
title: "Help migrating from NTFS to EXT"
date: 2010-10-05
forum: General Help
---

### Post by herregaarden on 2010-10-05
I recently converted from MS 2003 to Ubuntu 10.04.1 and i  wish to change the filesystem of all my data disks from NTFS to EXT but i have run into a problem. When i delete the old nfts partition and create an EXT4 partition, i can see that on the newly created partiton the used space is about 20gb. I used gparted for this. I have read that EXT reserves some space for root, but since all the disks i wan't to convert is only used for data and not OS, i see no need for the reserved space. I found some commands to turn of the root space but that did not work so i changed to resiserfs but that very slow, unstable and under limited development. I really hope someone can help me with this

---

### Post by ridgeland on 2010-10-06
Here are my notes when formatting a new 1TB external drive to ext3.  The 1TB drive is really 939GB but gparted reserved 37GB for root.  I guess "# df" would show it as fully available.  My answer was 
$ sudo tune2fs -m 0 /dev/sdg1
You are right do this on data only not OS partitions.

> Partitioning Freeing Reserved Blocks
/dev/sdg1 = WE Elements 1TB external hard drive
$ df
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sdg1               938898       200    891005   1% /media/USB-sdg1
$ sudo tune2fs -l /dev/sdg1 | grep Res
Reserved block count:     12209484
$ sudo tune2fs -m 0 /dev/sdg1
tune2fs 1.41.11 (14-Mar-2010)
Setting reserved blocks percentage to 0% (0 blocks)
$ sudo tune2fs -l /dev/sdg1 | grep Res
Reserved block count:     0
$ df
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sdg1               938898       200    938698   1% /media/USB-sdg1

---

