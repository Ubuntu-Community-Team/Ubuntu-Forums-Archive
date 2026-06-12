---
title: "I thought etx4 was better then NFTS"
date: 2009-07-18
forum: General Help
---

### Post by Hawaiisnowstorm on 2009-07-18
To answer the first thought that will come to mind for most of you, yes I know ext4 IS suppose to be better, but I some came to the end of this problem and can not figure out what happen.  So here I am and here is the issue.

New 1 TB Western Digital 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5

I formated it as NFTS in my Windows OS at first, but then decided I would format it as ext4 because I thought that would allow more space on the hard drive.  I used Gparted to delete the NFTS and format it as ext4.  

This is where the problem shows its head.  In NFTS format I about 931Bs free... on the ext4 format produces something odd.

According to Gparted I have 916GBs after 14GBs is used for formating.. okay no problem.  HOWEVER when I clicked on properties of the harddrive itself in the media folder is said I only have 870.1GBs free and that 46.8GB used is already being used.

There is no hidden folders no nothing on this hard drive, so why did I lose over 60GBs of space??  Did I miss a step in the formating of the hard drive??:confused:

---

### Post by ndiVianBG on 2009-07-18
Well, 
ext4 is just preserving a part of the file system for root (this is useful if its / so it dont fill up and graphical interface may become unusable)
You can turn this off 
tune2fs -m 0 /dev/YOURDRIVE

Viden

---

### Post by Hawaiisnowstorm on 2009-07-18
> **ndiVianBG said:**
>  
tune2fs -m 0 /dev/YOURDRIVE

I tried that and I received : 
```
hawaiidarkstar@HDS-Linux:~$ tune2fs -m 0 /dev/Music
tune2fs 1.41.4 (27-Jan-2009)
tune2fs: No such file or directory while trying to open /dev/Music
Couldn't find valid filesystem superblock.

```

I also tryed /dev/media/Music and just /media/Music and it gave me the same result.

---

### Post by jerome1232 on 2009-07-18
You have to point it to the actual device, the mount point is probably /media/music but the device path will be something like /dev/sdb1 or similiar (disks get letters a, b, c, d, etc and partitions are number so sdb1 would be second disk first partition)

To figure out where your device is at just check gparted it'll tell you. Alternativly you can check with the "mount" command.

```
mount
```

You may want to keep the paramaters the way they are though, they also help to prevent fragmenation of a full disk.

---

### Post by ndiVianBG on 2009-07-18
/dev/Music is not your drive. 
do this cat /etc/mtab | grep music | cut -b1-10
this will print the real name of your drive

---

### Post by Hawaiisnowstorm on 2009-07-18
I got it, thanks for the help!

> **jerome1232 said:**
> 
You may want to keep the paramaters the way they are though, they also help to prevent fragmenation of a full disk.

I just shrink it, so its not taking up 60GBs, rather like 15-20GBs. So I still have 900.04GBs to work with.

---

