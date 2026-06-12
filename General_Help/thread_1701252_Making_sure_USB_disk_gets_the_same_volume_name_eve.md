---
title: "Making sure USB disk gets the same volume name every time."
date: 2011-03-06
forum: General Help
---

### Post by Knightwise on 2011-03-06
Hi

I have an Android smartphone with a built in SD card with 8 gb's of storage that I use for podcasts and files.

Every night i plug the Android phone into my Ubuntu server via usb. The phone automatically goes into "mass storage mode" and Ubuntu 10.10 (Desktop Edition) auto mounts the SD card

The problem is , sometimes the SD card is mounted via the name "DESIRE" on  /media/DESIRE 
(i've given it this label when I had plugged in the volume into my mac via the finder)

Other times however it gives it a generic name 8013-3EFG or something  like that.

Since i've written up some Rsync scripts that backup files of the SD card to the server (and copy back fresh podcasts) its important that this "name" /media/DESIRE or media/8013-3EFG are consistent (otherwise my scripts won' work) 

Is there any way to do this ?

---

