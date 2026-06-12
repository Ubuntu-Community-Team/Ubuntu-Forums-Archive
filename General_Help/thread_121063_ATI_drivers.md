---
title: "ATI drivers"
date: 2006-01-24
forum: General Help
---

### Post by jerris86 on 2006-01-24
Has anyone use the latest ATI drivers version 8.21.7 from ATI.com.

I tried the automatic installation and i was asked to save the log file and do an aticonfig. I tried playing around and messed it up.

I tried doing an xorg-reconfigure and got the drivers back up. But it sucks more than the ubuntu provided drivers. And the problem still persist even after i switched back by installing the ubuntu drivers by referring to the ubuntu wiki.

The picture looks bad and the framerate looks jumpy.

I cant tell what is the problem because i updated to KDE 3.5 around the same time. I need some ideas on how to get smooth video playback

---

### Post by tomski on 2006-01-24
have you enabled DMA for EVERY harddrive & DVD/CD drive

---

### Post by jerris86 on 2006-01-24
I used automatix to enable DMA

when i type "hdparm /dev/hdc" in terminal it shows

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
_______________________________________________

when i type "hdparm /dev/dvd" in terminal it shows

/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
_______________________________________________

So i guess it is enabled. I do not know what the first command (hdparm /dev/hdc) does. I guess its for the harddisk. Anyone just correct me if i am wrong.

---

