---
title: "Install failure Ubuntu 9.10 errors on CD"
date: 2009-12-13
forum: General Help
---

### Post by Runamok on 2009-12-13
Lets see if someone can solve this.

I only have access to this laptop, and one external hardrive, and few SD cards..  I am currently posting in the forums by running off of a Ubuntu 9.10 **Live CD**.

I repartitioned and removed my old 8.04 OS, and then the installation of Ubuntu 9.10 hangs. The CD did not pass the error test.  There was 1 error in 1 file. I made the mistake of burning at max speed.  Doh!

Is there some way to burn a new Install CD from while running the Live CD?  This laptop only has one CD-RW/DVD burner, 2Gigs RAM.  However, I do have a backup of the ubuntu 9.10 ISO on my external drive.  I also have a few USB drives around, internet access, etc...

Any suggestions?

---

### Post by ram2500 on 2009-12-13
Considering that you are running off of RAM, I'd say that you cannot burn an install CD from a Live CD, at least without buffer underruns and total slowness. Try USB Startup Disk Creator (System > Administration) - however, your laptop must be USB bootable. 

This may not work as you said that you are running off of the same Live CD that has the error. It's worth a try.

---

### Post by aust77 on 2009-12-13
From what I know, nope. If you have a Live CD in your disk drive, logically you can't burn a disc while there is one within your drive. 

If it is a CD-RW disc you burned it on, even then you couldn't re-burn as it would crash the OS you are using.

I can help, but be more specific? Can you boot into Ubuntu at all without the Live CD? When I briefly encountered 9.10, I could hardly boot (with a good CD, oddly) but I booted in, burned a 9.04 CD and installed from there. So long as you can get your OS running without using a Live CD, you can burn the file and thus reinstall.


aust77

---

### Post by Runamok on 2009-12-13
I'll try booting without using the Live CD.  Be back soon, hopefully.

---

### Post by Runamok on 2009-12-13
Without the Ubuntu 9.04 CD, Ubuntu's Grub loader just gives an error 15.

However I can boot this laptop's BIOS does have a USB boot option in the BIOS.

---

### Post by Runamok on 2009-12-13
Taking a look at the USB Startup Disk. 

I have an SD card in a USB reader.  I also have the external HD.  Is it possible to repartition the HD and make a USB startup or install ubuntu onto it?

---

### Post by Runamok on 2009-12-13
Okay, I created a startup USB on the external hardrive.  Hopefully this will work without deleting all of the old files off of my external.  Wish me luck!

---

### Post by Runamok on 2009-12-13
I made USB startup disk on the external hardrive.  
The computer won't boot from this HD.  

Please Ubuntu Guru's help with this botched install!!!

---

