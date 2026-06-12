---
title: "LiveCD and External HD"
date: 2011-02-20
forum: General Help
---

### Post by kylek14 on 2011-02-20
Hey all,

I'm new to anything linux related and after doing some searching around and finding out that you can't run ubuntu from an external hard drive. Would it be possible, so to speak to run Ubuntu(and a couple of the other Ubuntu flavors) from a live CD and store any additional information (documents/images/additional programs/etc.) on an external hard drive and being able to run the full Ubuntu OS from anywhere with all my stuff (I'm guessing i may have to put /usr on the external hard drive if I decide to take this route?)

Just wanted to know if this was in the least case, worthy of attempting.

---

### Post by CHRSB on 2011-02-20
You sure can run Ubuntu from an external drive, but you computer must be able to boot from USB and it should be USB 2.0. What kind of laptop do you have?

I have it on both an external USB HDD and a a USB thumb drive.

---

### Post by kylek14 on 2011-02-21
> **CHRSB said:**
> You sure can run Ubuntu from an external drive, but you computer must be able to boot from USB and it should be USB 2.0. What kind of laptop do you have?

I have it on both an external USB HDD and a a USB thumb drive.

Actually I'm using a late 2008 Imac but I just wanna be able to use it with all my files in one central location whenever i move around to different computers (1 of my 5 computers or friends PCs, etc.) Tried booting the LiveCD from my thumb drive but it wouldn't work.

---

### Post by CHRSB on 2011-02-21
> **kylek14 said:**
> Actually I'm using a late 2008 Imac but I just wanna be able to use it with all my files in one central location whenever i move around to different computers (1 of my 5 computers or friends PCs, etc.) Tried booting the LiveCD from my thumb drive but it wouldn't work.

Sometimes we need to know when we are making our lives more complicated by trying to make it more simple. 

iMacs do not like USB booting even with rEFIt.
[http://refit.sourceforge.net/help/usb_disk.html](http://refit.sourceforge.net/help/usb_disk.html)

---

### Post by coldraven on 2011-02-21
Unplug or remove your hard drive.
Plug in your external USB drive.
Boot from Live CD and select your USB drive for the installation.
Change the boot order in your BIOS so that USB is above hard drive.
On my laptop I have set a window that appears for 5 seconds and gives me the choice of boot device.
After testing plug your hard drive back in.
I'm not sure how Ubuntu will respond if you plug it in to a PC that has vastly different hardware but it would be fun to find out.


For another option using a memory stick you can use System>Admin>Startup Disk Creator and tick "make persistence file". This would work on any machine that can boot from USB.

---

### Post by kylek14 on 2011-02-21
> **CHRSB said:**
> Sometimes we need to know when we are making our lives more complicated by trying to make it more simple. 

iMacs do not like USB booting even with rEFIt.
[http://refit.sourceforge.net/help/usb_disk.html](http://refit.sourceforge.net/help/usb_disk.html)

Sorry, that's what I meant. Probably should've included more information. But back to my original question. Would CD/ext. HD combo work?

---

