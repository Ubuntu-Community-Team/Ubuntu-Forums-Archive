---
title: "How Do I Install Windows 7 To A USB Flash Drive Using Ubuntu 10.10?"
date: 2011-02-13
forum: General Help
---

### Post by seanarickymurphy on 2011-02-13
I need to put Windows 7 on here, I have the ISO file. I don't have a cd-rom drive, only a USB port. None of the applications on here allow me to put Windows 7 onto the flash drive, I tried multiple commands to 'try' but they all failed. I searched online for most of the day, some said to try Win-To-Flash but of course it only runs in Windows, I tried it in wine only to get a error message. I also tried Windows 7 usb-dvd-download from cnet download. I ran them all in XP, Vista, 7 and what-not and they still come up with a error that keeps me from continuing. I also tried running the command "sudo dd if=/home/sean/Downloads/X15-65732.iso of=/dev/sdb1" without the quotes of course, but it appeared to only copy the contents and doesn't load Windows 7. I need to, I'm guessing, burn it to the flash drive. Its a Centon Data Stick Pro 4GB. I also tried USB Startup Disk Creator but it only works with Ubuntu .ISO's not Windows, and half the time or well basically all the time it never pulls up the ISO when i click on it I'm not sure why? I also tried Unetbootin, but it doesn't work with Windows. It only shows 'default' and 10. Clicking on Enter does nothing. Nothing loads. 

Anyone know how to install Windows 7 to a USB flash drive? Or should I try running a windows program from some other computer just to do this task?

---

### Post by C.S.Cameron on 2011-02-14
Microsoft has put a lot of effort keeping 7 from running on flash drive.

---

### Post by andymorton on 2011-02-14
You could get yourself an external disc drive that plugs in to the USB port. I'm not too optimistic about getting W7 on a memory stick.

---

### Post by pricetech on 2011-02-14
If you have the ISO, and it's legitimate of course, install in a VM and use it that way.

---

### Post by patelsagar on 2011-02-14
I had successfully managed to "burn" Windows 7 ISO file to my 4 GB USB pen drive, using UnetBootin (linux version of course). I don't know why it's not working for you :confused:

Are you sure you have enabled booting from USB device instead of HDD?

---

### Post by sydbat on 2011-02-14
> **pricetech said:**
> If you have the ISO, and it's legitimate of course, install in a VM and use it that way.This.

I have set up a few clients with Ubuntu host and Windows in [VMWare]("http://www.vmware.com/products/player/") and they like it. It even runs faster than a "full" install (as it were). You can even do a little 3D stuff now (which is very cool).

---

### Post by Mark Phelps on 2011-02-14
> **seanarickymurphy said:**
> Anyone know how to install Windows 7 to a USB flash drive? 

You ... don't!  As already said, MS has gone to a lot of trouble to ensure folks aren't walking around with portable versions of Win7.

Of course, you can copy the ISO to a flash drive, and that drive can be made bootable -- but then, you have a flash drive from which you can INSTALL Win7 -- not a flash driver from which you can RUN Win7.

---

### Post by stchman on 2011-02-14
It would have to be a HUGE flash drive.  You can use a 4GB flash drive to install Windows 7 on a computer, but not install.

---

### Post by C.S.Cameron on 2011-02-14
I have had 7 installed in VBox in Ubuntu on a Kingston Traveler 8GB.
I think I ran out of space the first second Tuesday.
I moved the VDI to a second flash drive.
I recall it was really slow.

It is possible to put XP on flash drive, (also slow).

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

The site is not always up.

---

### Post by patelsagar on 2011-02-15
Hey, sorry I forgot about something when I said I did make a Windows 7 USB bootable. Actually, you need to first format USB drive as NTFS.

I had followed this guide, glad to find it as bookmarked link :)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Now it should work for you :)

---

### Post by C.S.Cameron on 2011-02-15
> **patelsagar said:**
> Hey, sorry I forgot about something when I said I did make a Windows 7 USB bootable. Actually, you need to first format USB drive as NTFS.

I had followed this guide, glad to find it as bookmarked link :)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Now it should work for you :)

You also need to set the boot flag.

---

### Post by patelsagar on 2011-02-16
> **C.S.Cameron said:**
> You also need to set the boot flag.

Well, that part was in the guide already, but thanks for pointing that out :)

---

### Post by uRock on 2011-02-16
Sounds like a EULA violation. Maybe try asking on a Windows forum?;)

Thread Closed

---

