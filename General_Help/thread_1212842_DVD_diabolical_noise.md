---
title: "DVD diabolical noise"
date: 2009-07-14
forum: General Help
---

### Post by gueshew on 2009-07-14
I am having some issues with my dvd player which rattles very very loud when trying to read a dvd, or burning a CD-R.

Here is what it sounds like if that can help your prognosis:

[dvd_rattle.mp3 - 0.20MB]("http://www.zshare.net/audio/62644328a8a8432b/")

The DVD player WORKS! I have just trying booting my laptop this morning with a spare windows vista installation DVD and it loaded everything fine without any suspicious sound.

here is vlc's report after failing to read the dvd:

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: BREAKFAST_AT_TIFFANYS
libdvdnav: DVD Serial Number: 39787234
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/daboss/.dvdnav/BREAKFAST_AT_TIFFANYS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000134
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001449
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0032ab71
libdvdread: Elapsed time 93
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0032abc8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0032abc8)!!
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 93
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted


Also I have installed all the required packages from synaptic.

Running Ubuntu 9.04 kernel 2.6.30, previously 2.6.28 with the same issue.
Acer aspire 3680.


In advance, thank you for your help

---

### Post by Rhubarb on 2009-07-14
That sounds rather bad.

To me it sounds like the gears in your optical drive are borked.

I can't explain why it worked on your vista disc, but to me it sounds like a good idea to go and buy yourself a new optical drive.

---

### Post by gueshew on 2009-07-14
I am convinced this is not a harwdare issue, since the dvd worked great on other OS... But I agree with you, it sounds quite bad.

> **Rhubarb said:**
> That sounds rather bad.

To me it sounds like the gears in your optical drive are borked.

I can't explain why it worked on your vista disc, but to me it sounds like a good idea to go and buy yourself a new optical drive.

---

### Post by stinger30au on 2009-07-14
> **gueshew said:**
> I am having some issues with my dvd player which rattles very very loud when trying to read a dvd, or burning a CD-R.

Here is what it sounds like if that can help your prognosis:

[dvd_rattle.mp3 - 0.20MB]("http://www.zshare.net/audio/62644328a8a8432b/")



wow!
i wish more people did this

in a word, its stuffed

buy another!

---

### Post by gueshew on 2009-07-14
why would it work on windows and not ubuntu if it was really broken as you guys are saying?

> **stinger30au said:**
> wow!
i wish more people did this

in a word, its stuffed

buy another!

---

### Post by gueshew on 2009-07-14
bump

---

### Post by TeamJ on 2009-07-14
I have to say it doesn't sound broken, it sounds like software. it is as if the laser is going up and down or something.

but this may be an incompatibility thing

so buy a new one

---

### Post by t4thfavor on 2009-07-14
Does it only do it while trying to watch an encrypted dvd? maybe try it with a data dvd. The noise sounds like excessive seeks, which could be casued by drm on the disk sending the read laser on a wild goose chase.

---

### Post by gueshew on 2009-07-14
Thank you for your comments.


I have just tried:

-Backtrack CD: works
-Ubuntu live CD: works
-Data DVD: works and plays the mp3
-windows vista dvd: boots and works

Which leads me to exclude a hardware fault!

it sounds like and excessive seeking indeed, something happening only with encrypted dvds.

to make it clear, since I may have done a mistake, here are the packages installed on my pc:

libdvdread4
libdvdnav4
libdvdcss2
libdvdread-dbg
libdvdread-dev
libdvdnav-dbg

I have tried playing lots of dvds on all players known to mankind with the same results.

Also I just realized that my drive is not recognized as a CD-R/DVD drive by my pc (burning doesn't work), could it be related to my issue? 

sudo lshw -C disk

  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK8034GS
       vendor: Toshiba
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: AH30
       serial: Z6TNF130S
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=52b8b87b
  *-cdrom
       description: DVD reader
       product: CDW/DVD TS-L462D
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: AC01
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

---

### Post by vinutux on 2009-07-14
**Install libdvdcss2 from mediubuntu repo**

.

---

### Post by gueshew on 2009-07-14
> **vinutux said:**
> **Install libdvdcss2 from mediubuntu repo**

.

doesn't make a difference...

---

### Post by t4thfavor on 2009-07-14
Thank whoever came up with the dvdcss model of drm on DVD's. I think its going to be a problem for you as long as you have the drive.

Linux has a reverse engineered version of the dvdcss decoder, perhaps you have a dvd that does not conform to what the dev's expected it to do.

---

### Post by gueshew on 2009-07-14
> **t4thfavor said:**
> Thank whoever came up with the dvdcss model of drm on DVD's. I think its going to be a problem for you as long as you have the drive.

Linux has a reverse engineered version of the dvdcss decoder, perhaps you have a dvd that does not conform to what the dev's expected it to do.


I took what you said into consideration and tried a region 0 dvd, with no encryption, and it still didnt work, so it seems that the issue is not drm related....
this is making me crazy, I don't wanna switch back to winblows because of that issue.....
maybe a previous version of ubuntu...

---

