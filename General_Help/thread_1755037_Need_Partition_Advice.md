---
title: "Need Partition Advice"
date: 2011-05-10
forum: General Help
---

### Post by billyquizboy7 on 2011-05-10
Hello.  I want to repartition my pc.  To make a long story short, I upgraded to Natty, but absolutely hated it so I reinstalled 10.10.  I had a really hard time getting back to 10.10, however, and my partitions are not very fine tuned.  What I want to do is repartition without needing to reinstall 10.10 again.

I'm not too terribly linux literate, but as I understand it, I currently have three partitions:  

- 40 GB  (which has folders in it such as "bin" "boot" "cdrom" "dev" and "etc"...)
- 466 GB (which has my home folder in it--the folder with my account name) 
- 312 GB (which has folders in it such as "bin" "boot" "cdrom" "dev" and "etc"...)

The partition with my home folder in it is barely using 50 GB.  I want to allocate the rest toward the other large partition.  Any help you can give me would be awesome.

---

### Post by oldfred on 2011-05-10
I like to have several system partitions, so I can install the next versions and try it and I keep my last version. But I like smaller system partitions of about 25GB and keep all my data separate.

Are you looking for a new primary partition for windows? Otherwise you can make logical partitions inside your extended if you have one.

Post this so we can see what partitions are where:

```
sudo fdisk -lu
```

---

### Post by billyquizboy7 on 2011-05-11
Thanks for responding.  Here's the data:

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a0d0322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    78125055    39061504   83  Linux
/dev/sda2        78127102  1953523711   937698305    5  Extended
/dev/sda5      1937899520  1953523711     7812096   82  Linux swap / Solaris
/dev/sda6        78127104   989166987   455519942   83  Linux
/dev/sda7      1308704768  1918277631   304786432   83  Linux
/dev/sda8      1918279680  1937889279     9804800   82  Linux swap / Solaris
/dev/sda9       989167616  1295648767   153240576   83  Linux
/dev/sda10     1295650816  1308702719     6525952   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e272b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   488392064   244196001    7  HPFS/NTFS

---

### Post by oldfred on 2011-05-11
It looks like you have 3 Linux partitions and 3 swaps. Is the 10.10 your last install and sda9 & sda10. Which partition is /home and is it part of your 10.10 install?

Post this from the install you want to keep. It will show your fstab and what you are currently mounting as defaults.

sudo cat /etc/fstab

What is your goal. You can just delete the partitions you are not using and reuse or combine. You just cannot combine sda1 with any of the others as it is primary and everything else is in your extended partition.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

