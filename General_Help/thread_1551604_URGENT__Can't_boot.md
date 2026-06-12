---
title: "URGENT:  Can't boot"
date: 2010-08-12
forum: General Help
---

### Post by X5-655 on 2010-08-12
I'm about done with Linux again, I can't stand these constant screwups and information that changes and the change makes the old directions harmful to a new distro..

I installed VirtualBox, the one from Oracle with USB support, as I need to be able to get into XP and flash my cars computer with a USB cable program there..

I followed directions that I found, for what I COULD find, assign to ***** vboxusers, do changes to fstab for USB, etc..

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)

At the time while I was in a hot car with the laptop, thats all I could find...  Now it gets stuck at the Ubuntu splash screen at boot..

Originally when I logged off and back on after doing this, all was fine, but VBox still didn't use USB devices...

This is SERIOUSLY URGENT!!  This laptop is required for me to get my car working right now, so this affects my life, literally, cause I need to go to work..

---

### Post by X5-655 on 2010-08-12
Screwit, Single User Mode isn't working either..  It's time for me to just load the HP recovery utility and restore it back to Windows 7...

I miss the old days of Linux when these problems never really happened...

---

### Post by X5-655 on 2010-08-12
DAMNIT!!  Now HP Recovery Manager has decided that because I have Linux, I have to pay them $25 for recovery kit, because the recovery partition no longer actually formats hard drives for you, and the DVD the laptop burned when I bought it, failed burning, and you can't burn it twice!!

Screw you HP!!

---

### Post by earthpigg on 2010-08-12
that guide you chose to follow is what caused the breakage. 

> 2. Add the VirtualBox repo for ***Intrepid Ibex***. Click System > Administration > Software Sources. Click the &#8216;Third Party Software&#8217; tab. Click &#8216;Add&#8217; and enter:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) ***intrepid*** non-free

you installed virtualbox for ubuntu 8.10 - no surprise that the kernel module that VirtualBox attempted to install broke your system. i hate to break it to you, but this was your fault (and the fault of the author of that guide). would you expect Windows 7 continue to work if you started using a 3rd party registry editor for windows 98? Same thing here, when installing kernel modules intended for Ubuntu 8.10.

virtual box's official documentation is outstanding, i suggest you look there first in the future. and, download the .deb for VirtualBox from [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

you don't need to add any repositories or modify fstab to get virtualbox to work. i don't even think you needed to back when that guide was written -- at least, i do not recall doing any of that & i've always had USB support.

virtualbox's dialogues themselves will guide you through what little command line fu you need to do. installing dkms and whatnot to get guest additions to work. google is great, but reading what the software is telling you (if it is trusted) ought to always come first. certainly it ought to come before a guide that hasn't been updated in two years.

---

### Post by earthpigg on 2010-08-12
My mistake:

I forgot to include advice for your current predicament. 

Hold shift during boot up, this will bring you to the grub boot menu thingie.

Select the first "recovery" kernel. If that doesn't work, select one of the other kernels or recovery kernels. Once the computer boots, uninstall virtualbox and attempt to undo the other things that the guide told you to do.

That should clear things up for you.

And, what you described regarding HP's recovery software does indeed sound horribly frustrating. You could also try looking around the internet for an .iso image appropriate for your computer. I have no idea if this is legal.

---

### Post by X5-655 on 2010-08-12
The version of VirtualBox itself was for 10.04, I downloaded that .deb package for mine from their site...

But out of the box it wouldn't work with USB..

After much annoyances and unable to actually load the DVD for HP recovery (cylic redundancy check, this is the burned disc that you can only burn ONCE), I loaded my ubuntu live USB disk, loaded nautilus with root access, and removed the lines out of fstab, and that file in init.d or whatever, reboot, and viola, back in, and USB IS now working, because the group access was still in place (as for 10.04 specific instructions it's still valid, thus i didn't remove it)..  So log out and in doesn't work, a full reboot was required...  It said "or" in instructions, so to save time since i was in the hot sun i didn't do a full reboot..

Well it's working now, so i might need to keep my live USB disk with me at all times.  None of the recovery modes worked, single user didn't work either..  We need a REAL safe-mode, or something like NTs Last Known Good Configuration...

In the end though, Virtualbox provides poor USB syncronization and so my cars computer won't talk properly to any of the utilities..  Damn..

---

