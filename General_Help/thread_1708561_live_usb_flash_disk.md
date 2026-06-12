---
title: "live usb flash disk?"
date: 2011-03-16
forum: General Help
---

### Post by garyed on 2011-03-16
Can anyone tell why a flash drive needs to be a minimum of 2 gigs to burn an iso image for a live disk & yet a 700 mb CD will work just fine?

---

### Post by pqwoerituytrueiwoq on 2011-03-16
it does not i use my 1gb all the time for that
system->administration->startup disk creator
edit:
it is a Alcor Micro Corp. Transcend JetFlash Flash Drive

---

### Post by garyed on 2011-03-16
> **pqwoerituytrueiwoq said:**
> it does not i use my 1gb all the time for that
system->administration->startup disk creator

I'm just going by the what all the tutorials I've read say.
Every one so far says a minimum of 2 gigs for usb live disk from the iso file. 

I might just try 1 gig flash drive & see how it works.

---

### Post by Dave_L on 2011-03-16
I made a Live USB (10.04 netbook edition) with a 2GB drive, and the space used is only 709MB.  So a 1GB drive should be adequate.

Maybe the 2GB recommendation is in case you use the option to reserve space on the drive for saving data.

---

### Post by sml156 on 2011-03-16
I just did it with Linux-live USB Creator ( [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) ) I even managed to get 200 MB of persistence it said I could go up to 300 MB (I had to to uncheck all the check marks to get it ) but I dident feel like pushing it . Oh by the way I am using it now , the only thing I have to figure out is the grub menu I am still searching for that
 
The more I figure out If I remember I will just keep editing this
 
Press the TAB key while it is booting up the USB will get you into persistent mode but I still got to find out the best way to get it to boot with the grub
 
I tried to change the way it loads but there was not enough disk space to move the grub , I guess that could be one reason to use a 2 gig usb otherwize it works fine probally better than a cd because you can save some stuff like background and your internet settings

---

### Post by garyed on 2011-03-17
I cleaned out a 1 gig usb drive & did it too.
It boots Lucid 10.04 & works O.K. so far for me too.
If I get a grub menu working I'll post back.

---

