---
title: "Cannot connect my Windows mobile 6.5 touch pro2 to ubunto 10.10"
date: 2010-10-26
forum: General Help
---

### Post by jordanthompson on 2010-10-26
I read somewhere that this was supposed to be very easy in 10.10.  I have not experienced this yet :-)  I am expecting to be able connect my phone via USB and voila! have it appear as another USB drive that I can browse to.  I have no interest in syncing the phone and OS, I just want to be able to browse the contents of the phone.

When I connect the phone, the phone lights up and begins to charge, but I cannot browse to it from Ubuntu (another drive is not added to the list of drives.)

When I connect a USB drive, however, it appears as I would expect.

Any suggestions?

thanks in advance...

---

### Post by requeth on 2010-10-26
Try running the command lsusb to see if the device is showing up. Adding a -v gives a rediculous amount of information so a 'lsusb -v | more' may work better for you. Post back with the results and I'll keep an eye on this.

---

### Post by jordanthompson on 2010-10-28
OK - I fixed this by using synce-trayicon:
sudo apt-get synce-trayicon

One thing to note: the icon will not appear unless:
1) the phone is connected
2) the phone is TURNED ON(!)

---

### Post by jeebustrain on 2010-10-28
I have the same phone (w/ the same OS) and have no problems connecting and seeing the SD card as a drive. 


Make sure in the USB settings on the phone (in the control panel), you don't have it set to automatically use ActiveSync. When you plug it in, it (the phone) should prompt you to either mount it as a drive or using activesync

---

### Post by jordanthompson on 2010-10-31
Looks like I was to hasty in marking the thread as solved :-(

I can browse to the phone, and there are two icons available:
Documents and Filesystem.  When I try to browse into either one of them, I get:
The folder contents could not be displayed.
Sorry, could not display all the contents of "Filesystem": An unspecified failure has occurred

---

### Post by jordanthompson on 2010-10-31
> **jeebustrain said:**
> Make sure in the USB settings on the phone (in the control panel), you don't have it set to automatically use ActiveSync.


That's what did it!  I didn't realize that active sync was always trying to connect!

thanks

---

