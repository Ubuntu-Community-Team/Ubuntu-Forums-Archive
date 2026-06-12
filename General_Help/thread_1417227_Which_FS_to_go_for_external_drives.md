---
title: "Which FS to go for external drives?"
date: 2010-02-27
forum: General Help
---

### Post by rahilm on 2010-02-27
I have a Seagate 250GB Extrenal Hard disk. I am thinking of creating a linux only partition to store backups of my system. So which FS should i go for the ext's, XFS, REISERFS etc etc.

The partition will be primarily be used for backups and occasionally for storing movies and iso files.

Also i am thinking of creating a 5-7 GB partition on the disk for testing Lucid. I'll go for ext4 certainly but is it safe to install an entire OS on the disk? It will also serve as the ultimate portable OS. Will it corrupt the disk or make it wear away quickly (like flash disks do)??

---

### Post by 23dornot23d on 2010-02-27
I use external USB hard drives nearly all the time ....... for over 2 years now .......

I use them for backing up photos of which I have thousands ..... and they work really well

I also have a couple of operating systems on each one  ...... which work very well too

I do graphic design and 3D work ........... 

( but do not do games .... so cannot say if the decrease in transfer rates will be an issue here ) 

______________________________________________________________________

One is a 250gb USB drive .......... this picks up every time ........ I boot up ......

The other an Iomega 1 terrabyte drive .......... and due to a lag on discovering the USB drive 
the grub will not show up   ..... on an initial boot up .............. 

So on boot up.......... to get this to work properly ..........

I have to go into setup and just do a configuration save ...... by the time I have come out it has picked up and will boot up ok ........ 
its not ideal but it works ..........

As for the partitioning ....... I have NTFS for around the first 60 gig on both the USB drives ....   

Then I use  ext 3  .... for linux ..... partitions ..... for the rest ......... 

on my first USB drive I did a mix of NTFS ext2 ext3 reiserfs ..... but after 2 years and me messing
with numerous operating systems on it ..... it has got a little messed up ....... everything still reads ok from it ....... 
but I have backed all my photos onto the Terra drive and they all read perfectly well off of it ........... 

At some point I might reformat the 250Gb ,,,, but it is still serving its purpose as a backup system ....... they are
not that expensive now and the cheapest form of storage per megabyte .......... so I think they are great,

 I would personally use them till they are full then as time progress's and they get cheaper
just go out and buy another one ....... later ...... on ..... 

My latest is a 500 Gb seagate that is split into 4 partitions ....  first 60 Gb NTFS and 3 partitions ext4 
and upto now everything seems to be ok ........ but I have only had this 2 months ......... 

This I added onto a very old Acer Aspire laptop that only had a 40gb internal hard drive ..... 
[IMG]http://i48.tinypic.com/kefzuc.jpg[/IMG]

now it has a new lease of life and I run Linux Mint on it .......... 

Hope that this helps in some way ........

---

### Post by rahilm on 2010-02-27
> **23dornot23d said:**
> I use external USB hard drives nearly all the time ....... for over 2 years now .......

I use them for backing up photos of which I have thousands ..... and they work really well

I also have a couple of operating systems on each one  ...... which work very well too

I do graphic design and 3D work ........... 

( but do not do games .... so cannot say if the decrease in transfer rates will be an issue here ) 

______________________________________________________________________

One is a 250gb USB drive .......... this picks up every time ........ I boot up ......

The other an Iomega 1 terrabyte drive .......... and due to a lag on discovering the USB drive 
the grub will not show up   ..... on an initial boot up .............. 

So on boot up.......... to get this to work properly ..........

I have to go into setup and just do a configuration save ...... by the time I have come out it has picked up and will boot up ok ........ 
its not ideal but it works ..........

As for the partitioning ....... I have NTFS for around the first 60 gig on both the USB drives ....   

Then I use  ext 3  .... for linux ..... partitions ..... for the rest ......... 

on my first USB drive I did a mix of NTFS ext2 ext3 reiserfs ..... but after 2 years and me messing
with numerous operating systems on it ..... it has got a little messed up ....... everything still reads ok from it ....... 
but I have backed all my photos onto the Terra drive and they all read perfectly well off of it ........... 

At some point I might reformat the 250Gb ,,,, but it is still serving its purpose as a backup system ....... they are
not that expensive now and the cheapest form of storage per megabyte .......... so I think they are great,

 I would personally use them till they are full then as time progress's and they get cheaper
just go out and buy another one ....... later ...... on ..... 

My latest is a 500 Gb seagate that is split into 4 partitions .... NTFS and ext4 and upto now
everything seems ok ........ but I have only had this 2 months ......... this I put onto a very old
Acer Aspire laptop that only had a 40gb internal hard drive ..... now it has a new lease of life
and I run Linux Mint on it ..........

Hope that this helps in some way ........

That's a great reply...without any conclusion... all i got from it is that it is perfectly safe to install OS on an external drive. But it does not address the initial query?
Thanx for the help

---

### Post by 23dornot23d on 2010-02-27
My conclusion is that the USB drives are perfectly good for backups and it does not really matter
too much which one of the file systems you use ...... non have failed ......

The File System I would choose now is the latest as I put it on my latest drive  ...... ext4 as I said ...... but
I cannot give a better response than this has I have only used it for 2 months ..... 

As for wearing out ...... this is subject to the mechanics of the drive ..... and what type of environments 
it is put in and out of ........ and how often it gets used ..... one of mine has been used constantly for 
2 years .....

---

### Post by dcstar on 2010-02-27
> **rahilm said:**
> I have a Seagate 250GB Extrenal Hard disk. I am thinking of creating a linux only partition to store backups of my system. So which FS should i go for the ext's, XFS, REISERFS etc etc.

The partition will be primarily be used for backups and occasionally for storing movies and iso files.

Also i am thinking of creating a 5-7 GB partition on the disk for testing Lucid. I'll go for ext4 certainly but is it safe to install an entire OS on the disk? It will also serve as the ultimate portable OS. Will it corrupt the disk or make it wear away quickly (like flash disks do)??

EXTx - good for mixed file sizes and large file quantities (which is why it is a Linux default) and reasonable performance. Does auto checking.

Reiserfs - Better performance for large file sizes (in my experience) and seems pretty stable. Maybe not that well optimised as EXTx for heaps of smaller files. Auto checking is a pain..... a slow pain....

XFS - All reports I've seen say it is quite a good performer, I have only have a little experience with it so I'm not qualified to say much more.

An external USB drive will be slower than an internal drive, an external eSATA drive should be just as quick as an internal SATA drive - there is no "wear" issue as the drive inside the enclosure is exactly the same as the drive inside a PC.

---

### Post by rahilm on 2010-02-27
thanx Guys..i may proceed with ext4 in both cases

---

