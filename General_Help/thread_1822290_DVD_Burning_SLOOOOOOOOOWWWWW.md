---
title: "DVD Burning SLOOOOOOOOOWWWWW"
date: 2011-08-10
forum: General Help
---

### Post by LuridCinema on 2011-08-10
I tried this in the Multimedia forum, but no luck..Maybe I can get some help here. Sorry for double post.

Im getting very slow DVD burning. Quite often in Turbojet2 or using  growisofs or whatever, Im getting 0.5x DVD burning speeds.
I set the burn speed to 12x on Turbojet, but it hovers from 0.5x to maybe bursts of 5x.
I will get maybe 9 minute burn times in Brasero for single DVDs but 15 to 25 minutes in  Turbojet2 and longer using growisofs or other CLI burning when doing multiple DVDs.

Im running 11.04 on a box w/ SATA drives, SATA DVD-RW's 12gb of Ram an Intel I-5 4 core processor

I have played w/ hdparm settings but no luck...I tried the below

```
root@p9-TH55-HD:/media/2tb# **hdparm -d1 -c1 -a8 -u1 /dev/sr2**

/dev/sr2:
 setting fs readahead to 8
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default) 
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     =  8 (on)

```I tried 
Adding the following to the end of your hdparm.conf 
/dev/hdc { dma = on }

NOTHING works !! GRRRRR

any ideas ???

I dunno if sdparm needs changing or what...

---

### Post by LuridCinema on 2011-08-16
* 				Would a SATA controller card solve this ? Too bad I cannot just open  up 3 instances of Brasero . I think the main issue is when burning  multiple copies, it slows things down 			*

---

### Post by collisionystm on 2011-08-16
Have you checked the DVD itself to see if it supports a higher burning rate? For instance if you use a 4x cd-rw you will only burn at 4x. You must buy a 52x to burn at 52x

---

### Post by LuridCinema on 2011-08-18
Yes, the DVD writers are rated 16x for DVD-R. I get from 0.3X to 4.7X in small bursts. When burning 3 DVDs It goes from 15 to 25 minutes burn time

---

### Post by CMDR:ZOD on 2012-01-31
[LEFT]I to have the same issue. In windows I can burn 2 discs at once in about ten minutes, while in linux burning the same image on the same two drives takes almost half an hour! All the time the speed is very unstable, according to Turbojet2. Anyone have any ideas?
[/LEFT]

---

### Post by CMDR:ZOD on 2012-04-13
Bump

---

### Post by RJARRRPCGP on 2012-04-13
I just Googled, it looks like an issue with libata or hdparm itself. 

Unfortunately, it likely means that libata and/or hdparm are required to be recompiled.

---

### Post by CMDR:ZOD on 2012-04-15
I just solved the issue by using ImgBurn in wine. I use one instance for each writer and it seems to be working great so far. One writer is at 11x and the other at 15x simultaneously, far better than Ive seen in TurboJet2. :guitar:

---

