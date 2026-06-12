---
title: "Can't get Ubuntu to work on my hp laptop"
date: 2011-08-02
forum: General Help
---

### Post by procheese on 2011-08-02
Hey, I am an ubuntu newbie so bear with me.

I am trying to boot my laptop ( hp pavillion dv6t quad edition ) with a  live usb disk of ubunto 10.04 created with universal usb installer.  The  laptop has a hard drive problem and cannot boot into windows, so I was  going to try to save some files by booting into Ubuntu and copying the  files over (if I could mount the drive).

I get to the ubuntu screen and hit enter to run ubuntu from this usb.  Then after a while it gets stuck in a loop of errors:

ata1.00: failed command:  Read FPDMA QUED
ata1.00: cmd 50/08:00:00:40:82/00:00:4a:00:00/40 tag 0 ncq 4096 in
res 41/40:00:80...
status: {DRDY ERR }
error: {UNC }

(Like I said I am a newbie, the errors go by fast and I don't know how  to pause them to type them down.  However, it looks like it won't boot  because of the hard drive problem.  Does Ubuntu need a good hard drive  to boot?  I thought it would just use the usb drive like its own HDD...)

It boots fine on my home PC.  Any ideas?

---

### Post by Mark Phelps on 2011-08-02
IF I recall correctly, some else tried installing Ubuntu to a similar model laptop and they couldn't do it.  Something about the hardware being "too new" for Ubuntu.

An alternative would be to do remove the hard drive from the laptop, and using an interface adapter, hook it up to your other PC.  If the drive is readable at all, that may give you a way to recover some files.

---

### Post by akand074 on 2011-08-02
I doubt it's too new. As those errors seem hard drive related only. And really there is no hardware that won't allow Ubuntu to even boot, including graphics cards.

I've never actually made a live USB. I've always used a liveCD and never had any trouble. Might want to give that a try if no one knows your issue off hand. There is a chance you installed Ubuntu on the USB rather than turn the USB into a bootable image of the Ubuntu installer. Which could have been the issue, but I don't think that's the case.

---

### Post by JC Cheloven on 2011-08-02
You're correct. In principle, the live cd/usb disk should boot despite a faulty hard disk over there. 

Taking out your hard disk and triyng to read from it in a running system would be an option, as suggested.

Also, you may try to use the [SuperGrubDisk]("http://www.supergrubdisk.org/") to boot in windows and proceed from there (if successful).

---

### Post by omelette on 2011-08-02
Sounds to me like its your USB install that is corrupt.  I installed Natty 11.04 yesterday on a mini-pc via the USB route ('cos it ain't got a drive) and first time round, irrespective of the USB menu option I would choose, it would eventually lock up, telling me it couldn't mount the filesystem.  After a second try at making a bootable USB with UNetbootin, everything worked as expected.

---

### Post by wannabegeek on 2011-08-02
I have had problems with the Boot-able USB creator in 9.10....Sometimes it worked and other times it didn't.

Try again, and try different brands of USB, they are not all the same in quality,speed, blah.blah...

You should be given an option to make a space on the USB for saving use settings and stuff. I found that helpful but it may make the process more complicated.

---

### Post by procheese on 2011-08-04
Thanks for the replies everyone,

Regardless of saving the files, does anybody have an idea on how to get Ubuntu to even work on this laptop?  Could it just not be compatible?  I am pretty sure it is not the USB since I have now used it on two different computers flawlessly.  I somehow suspect there could be some boot parameters I could change to make it work, but I don't really know what or how.

---

### Post by JC Cheloven on 2011-08-04
> **procheese said:**
> Thanks for the replies everyone,

Regardless of saving the files, does anybody have an idea on how to get Ubuntu to even work on this laptop?  Could it just not be compatible?  I am pretty sure it is not the USB since I have now used it on two different computers flawlessly.  I somehow suspect there could be some boot parameters I could change to make it work, but I don't really know what or how.
When you boot off live usb, and get into the menu "Try Ubuntu without installing / Install Ubuntu /... / etc", you can press F6 for some boot options. 
Please mark the options "noapic" and "nolapic" (arrows to move among options, space to mark an option, esc to close the menu), and boot by choosing "Try Ubuntu without installing". 

Let's see if that helps.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
i actually had a faulty hdd that would not allow me to boot with it plugged in (used usb drive)
worked fine once i unplugged the bad drive
you can always try a natty live cd/usb

---

