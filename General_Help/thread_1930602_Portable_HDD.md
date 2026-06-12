---
title: "Portable HDD"
date: 2012-02-24
forum: General Help
---

### Post by esky64 on 2012-02-24
I have a 16gb ubb stick like most I guess when inserted it just starts and works.
I have a 500Gb Portable HDD that I would like to work the same way.
Why is, are they regarded differant?
Why don't portable HDD just work the same way as a USB stick?
How can I make it work the same, what settings do I need to change?
seams silly to me not working the same !!
Thanks 
Chris

---

### Post by raja.genupula on 2012-02-24
[http://superuser.com/questions/320084/speed-difference-between-portable-hdd-and-usb-flash-drive](http://superuser.com/questions/320084/speed-difference-between-portable-hdd-and-usb-flash-drive)

[http://forums.techarena.in/hardware-peripherals/1429913.htm](http://forums.techarena.in/hardware-peripherals/1429913.htm)


[http://www.askageek.com/2006/10/08/difference-between-a-portable-hard-drive-and-a-flash-drive/](http://www.askageek.com/2006/10/08/difference-between-a-portable-hard-drive-and-a-flash-drive/)

---

### Post by Paqman on 2012-02-24
How are you plugging your hard drive in? USB? SATA? What is it that doesn't happen when you plug it in? "Doesn't work" isn't much to go on!

---

### Post by esky64 on 2012-02-24
I guess that is not the way I really ways trying to ask the question but some good reading 
why will ubuntu reconise my usb stick work with it read write when I can only read from my HDD if i'm lucky

---

### Post by Mark Phelps on 2012-02-24
Without further info on your hard drive, we can only guess ...

But, one thing that CAN explain the different is filesystem formatting.  USB sticks are nearly always formatted by default as FAT or FAT32.  USB hard drives are FAT32 or NTFS.

If you're using an NTFS-formatted USB hard drive and simply unplug it, when you go to plug it back in, especially if that is to a PC running Linux, the filesystem was marked as "dirty" and, to prevent further damage to it, Linux will now ONLY mount the filesystem in READ mode.

To fix this, you often have to connect the USB hard drive to a MS Windows PC and run CHKDSK on the drive's partition(s).

---

### Post by mcduck on 2012-02-24
Also there's always a great way to find out what exactly is happening (or going wrong) when plugging in a removable drive or other device...

Just open a terminal, run "*tail -f /var/log/syslog*", and then plug in the device. You should see messages about how the device is recognised outputted into the terminal. Post them here if you need help interpreting them...

---

