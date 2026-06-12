---
title: "Anormal speed transference external HD"
date: 2009-07-17
forum: General Help
---

### Post by SergioRuiz on 2009-07-17
Hello there,

I have a PC with Kubuntu and two hard disk drives. These are the partitions...

# /dev/sda4
UUID=dcf96096-c7dd-47c2-a44e-bbfefdd5ebbc /home           reiserfs relatime        0       2

# /dev/sdb1
UUID=CEDCEB66DCEB4775 /media/datos    ntfs    defaults,umask=007,gid=46 0       1

When I copy a big file to an external USB HD I get the following average speeds from the different partitions...

sda4 -> 4.5 MiB/s
sdb1 -> 30.0 MiB/s

This are the hdparm -tT results

/dev/sda4:
 Timing cached reads:   1008 MB in  2.00 seconds = 503.77 MB/sec
 Timing buffered disk reads:  138 MB in  3.01 seconds =  45.78 MB/sec

/dev/sdb1:
 Timing cached reads:   1488 MB in  2.00 seconds = 743.90 MB/sec
 Timing buffered disk reads:  182 MB in  3.03 seconds =  60.15 MB/sec

Any clue? Thanks in advance.

Sergio Ruiz

---

### Post by blueridgedog on 2009-07-17
Sergio:

It appears that hdparm gives the performance of the drive itself.  Given that it appears that the slower drive is indeed running at 75% of the speed of the faster drive, it fails to explain the slower drive moving files at 15% the rate of the faster drive (even with a CPU intensive file system like ntfs).  Could it be the implentation of reiserfs you are using?  Can you add CPU load numbers to the comparisons?  Do you have another partition on /sda that is ext3 or ext4 that you can compare the speed to?

---

### Post by SergioRuiz on 2009-07-19
> **blueridgedog said:**
> Could it be the implentation of reiserfs you are using?  Can you add CPU load numbers to the comparisons?  Do you have another partition on /sda that is ext3 or ext4 that you can compare the speed to?

Thank you blueridgedog. I don't know how to find out the ReiserFS implementation I'm using... Regarding CPU load here are a couple of screen captures.

Copying FROM NTFS partition...

[]("http://ubuntuforums.org/%5BURL=http://img150.imageshack.us/i/fromsdb1.png/%5D%5BIMG%5Dhttp://img150.imageshack.us/img150/5484/fromsdb1.th.png%5B/IMG%5D%5B/URL%5D")[[IMG]http://img150.imageshack.us/img150/5484/fromsdb1.th.png[/IMG]]("http://img150.imageshack.us/i/fromsdb1.png/")

Copying from ReiserFS partition...

[[IMG]http://img300.imageshack.us/img300/6733/fromsda1.th.png[/IMG]]("http://img300.imageshack.us/i/fromsda1.png/")

Thank you so much for your help...

Sergio Ruiz

---

### Post by blueridgedog on 2009-07-19
What other partitions are on sda?

---

### Post by SergioRuiz on 2009-07-19
There is another NTFS partition in the same HD... I've done a test and it seems to work fine, so I guest hardware issues are descarded...

[]("http://ubuntuforums.org/%5BURL=http://img198.imageshack.us/i/fromsda2.jpg/%5D%5BIMG%5Dhttp://img198.imageshack.us/img198/2182/fromsda2.th.jpg%5B/IMG%5D%5B/URL%5D")[[IMG]http://img198.imageshack.us/img198/2182/fromsda2.th.jpg[/IMG]]("http://img198.imageshack.us/i/fromsda2.jpg/")

This is the complete fstab file...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b6b27851-b758-43ea-ad44-8485fd94e704 /               reiserfs notail,relatime 0       1
# /dev/sda4
UUID=dcf96096-c7dd-47c2-a44e-bbfefdd5ebbc /home           reiserfs relatime        0       2
# /dev/sdb1
UUID=CEDCEB66DCEB4775 /media/datos    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=0484C3A584C39796 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7cbed3c5-7f93-4d18-993c-04affe43e96d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by metacell on 2009-07-19
Have you checked if DMA is enabled on both HDs?

---

### Post by blueridgedog on 2009-07-19
> **SergioRuiz said:**
> There is another NTFS partition in the same HD... I've done a test and it seems to work fine

I suspect it is the file system or the number of fragments on the system.

If you can backup the partition and reformat it to ext3, I would bet your performance would increase.

---

### Post by moster on 2009-07-19
I experienced enormous slowdown when I downloaded some movies with Transmission (torrent) and then try it to copy on USB disk or another partition. 

I was believing that ext3 do not fragment much but in this case it was horribly fragmented because transmission do not have preallocation.

Maybe your situation is similar. check fragmentation of specific files by running this in terminal.

```
sudo filefrag -v YourFile 
```

---

### Post by SergioRuiz on 2009-07-20
That's it, Moster! You were right... It is a Transmission issue :-(... I copied a big file to a different location, then transfer to external drive was perfectly fine. Anyway I'll format the drive to do some "cleanup" of old things we don't use anymore...

Problem solved, thank you so much!

All the best,

Sergio

---

