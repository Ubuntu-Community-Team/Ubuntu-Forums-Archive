---
title: "Startup USB disk"
date: 2009-11-06
forum: General Help
---

### Post by YigalB on 2009-11-06
I am trying to make a bootable Ubuntu from USB disk, 2GB.
I placed installation CD of desktop 9.10 (I am not sure why do I need that - can't the utility get all the data from the web?)

I run the "Make startup disk". It recongnized the CD and the USB disk.
The USB disk (/dev/sdb) shows  "!" and it says that this device should be formatted.
However, when I press the format button - nothing happen.

Any idea why?
Is there another way to create bootable Ubuntu USB disk?

Another question: will it work with any PC? how does it handle the drivers - after all, there are many types of hardware out there.

---

### Post by MelDJ on 2009-11-06
try [UNetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by Mighty_Joe on 2009-11-06
> **YigalB said:**
> However, when I press the format button - nothing happen.


I had the same problem with the format button. The format button problem is a [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/457737") in Karmic. 
MelDJ's suggestion is a good one.  
If you want to format your drive from the Live CD, click on System->Administration->Partition Editor.  From the device drop-down, select your USB drive.  Click on Device->Create Partition Table.  Click the "create" button.  Now your disk should have one unallocated partition.  Right-click on the unallocated space and select "New" from the menu.  Select "fat32" as the file system and click on "add".  Click on "apply".
The USB Creator should work now.

---

### Post by Bunnybugs on 2009-11-06
The format button in the dick creator is some kind of a bug...

Use NetBootIn....

With that, you can download the Ubuntu .ISO file, and install it to your USB...

BUT, don't forget: You have to rename the ISOLINUX-folder to SYSLINUX, delete the SYSLINUX.CFG-file from the USB-Root, enter your renamed SYSLINUX (used to be ISOLINUX)-folder, find the ISOLINUX.CFG-file, and rename it SYSLINUX.CFG

Reboot your computer, and set your BIOS to use the USB-device as first bootingdevice, on top of your HDD...

From here, you can follow the instructions, if needed!

EDIT: You can find UnetBootIn in the repositories (Applications>Ubuntu Software Center>> "Search for Unetbootin"

---

### Post by YigalB on 2009-11-07
Thanks guys: NetBootIn is working for me - I can boot.
However, I was sure I will get a working disk, as any IDE/SATA disk. It appears that this disk is working like a live CD, so performance is slow (a lot of access  to the flash).
Now I would like to progress:
1- is there a way to run the OS from the DRAM (assuming there is a lot of DRAM), similar to "RAM disk" approach?
2- Is there a way to force Ubuntu to treat the USB disk as a regular disk and install all the OS on it?

---

### Post by brucenduane on 2009-11-07
If you are looking for a ram based Linux OS.

I is a live CD Linux like Ubuntu

Loads completely into ram (256MB minimum)
Can be installed on a USB flash.
Run from a multi-session CD.

Try Puppy Linux 4.3.1

[http://puppylinux.com](http://puppylinux.com)

-bruce.

---

### Post by amopresunto on 2009-11-07
From the UNetbootin page....
> If you are having trouble with the Linux version, try the Windows version, it usually works better.

Why is this?  I unfortunately find this to be generally true, which is why I have never fully committed to Linux.  I would like to ditch Windows, but I have never been given enough of a compelling reason to do so from any Linux distribution.  Ubuntu has come the closest, but it still is not enough.

Sorry for the rant and going off topic.  I really came here because I was having the same trouble with the USB Startup Disk Creator.:confused:

---

### Post by YigalB on 2009-11-07
> **amopresunto said:**
> 
Sorry for the rant and going off topic.:

Don't be sorry, and it's not off-topic. This is the major topic - I agree with you that Ubuntu is close, but it's not there, mainly because of the level and maturity of the applications, such as this.
Ubuntu is superior from many aspects, but most of the applications are just not mature enough to be distributed.

---

### Post by amopresunto on 2009-11-07
Thanks, YigalB.

> **Bunnybugs said:**
> You can find UnetBootIn in the repositories (Applications>Ubuntu Software Center>> "Search for Unetbootin"

Thank you for this.  The version I downloaded from the website did not work.  The Ubuntu Software Center version worked perfectly.

---

### Post by Mighty_Joe on 2009-11-09
> **amopresunto said:**
> Why is this?  I unfortunately find this to be generally true, 

There are lots of reasons, many covered in [this document]("http://linux.oneandoneis2.org/LNW.htm").  The Linux world is very different from the Windows world.  Linux is very good for some tasks.  Other tasks, not so much. Use the right tool for the job.

---

### Post by Mighty_Joe on 2009-11-09
> **YigalB said:**
> 
2- Is there a way to force Ubuntu to treat the USB disk as a regular disk and install all the OS on it?

If you boot up the LiveCD and start the install process, you'll see the USB drive as a normal disk and you can install to it.  Just make sure to install Grub to the USB drive.  I posted a link to detailed instructions [here]("http://ubuntuforums.org/showthread.php?t=1193680").

---

### Post by leorolla on 2009-11-10
Two different things:

A installation "CD" to be run from the USB.

An installed Ubuntu operating system.

The second one will probably have the drivers set to your hardware... and you will have to work that out. You can make an Ubuntu install to USB2 from USB1, which should be the Live CD.

To get the first one, the simplest way is to have Karmic running somewhere (if you have Windows and 5GB free, just do a Wubi install, it takes 25min), and use the Usb Creator tool (System -> Administration -> USB something) to "burn" the downloaded Ubuntu ISO to USB1. 

Then boot from USB1, open the Desktop, insert USB2 and see if it mounts it, and then install to USB2.

When producing USB1, you can also at this point use S->A->Disk Utilities to partition and format USB2, so that it will be ready for the installation.

---

