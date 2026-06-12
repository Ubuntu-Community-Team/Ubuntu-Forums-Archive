---
title: "How do I start from scratch?"
date: 2012-01-01
forum: General Help
---

### Post by stroudmichael1115 on 2012-01-01
Hello I am running Ubuntu 10.10, I have recently download allot of things and messed around even more so. my goal is to reload Ubuntu.

I don't have a cd or external hard drive or anything to simply put ubuntu on and set to boot off of. my question is, how do I, or can I, reload ubuntu and start from scratch with just the Internet and my hard drive? I have been kind of thinking, maybe I could download 10.10 make a partition then just wipe my current os and replace it with the new clean one. Or I was wondering if there was a command or something? I am not really sure how to go about doing any of this, I tried Googleing it but I figured that one of you would know exactly what to do and be able to give me some pretty easy instructions. I would really like the partition idea because then I could just reload ubuntu when even I wanted with just my system. Thank you very much.

---

### Post by rsvancara on 2012-01-01
Do you have another system that you could put the Ubuntu distribution on a USB thumb drive?  I have several systems that do not have a CDROM drive, that I have to configure this way.  Also an external USB CDROM drive can work as well.  Just depends on your system?

What kind of system are you trying to re-install?

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by Synoc on 2012-01-01
to boot without a CD, or another hard drive... it CAN be done. there is a netowrk protocol called pc99 that allows for a network boot called a PXE boot. but it requires you to have another PC to serve you the operating system. 

other thing that might work (I've never tried) would be to tell GRUB to load from another partition on which you would have the Ubuntu live image (I'd imagine the same way you do a live boot USB), but that is a computer trick I have never tried and editing GRUB is NOT my forte. 

PXE booting would be more complex than tricking your PC to think your hard drive partition is a USB drive... I think... and would still require a Linux CD to install the OS. IF you can trick the computer, it SHOULD more or less treat the install like a standard install past that point, but I don't know.

my advice, get a CD, beg for one if you have you, it would be much easier.

---

### Post by sleepingdragon on 2012-01-02
UNetbootin will take a Ubuntu ISO and make it work on a USB thumb drive. You'll need a second machine to do it, but you'll get the standard Ubuntu install (32/64 bit) onto your CDROM-less machine (assuming you can boot from USB). There are versions for Windows, Linux and Mac.

Install UNetbootin (on the second machine), and plug in your thumb drive *before* starting UNetbootin, then download the Ubuntu ISO. 

Start UNetbootin, select  "Diskimage" (it should default to ISO) and go find the downloaded ISO file. You can then select the USB thumb drive from the drives offered. 

Click on OK then wait for the ISO to transfer to the thumb drive. When done (click on EXIT to finish), you can use the thumb drive as a boot drive on your CDROM-less machine and go through the usual install process.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Lars Noodén on 2012-01-02
It's also possible to boot the ISO image straight from Grub:
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

