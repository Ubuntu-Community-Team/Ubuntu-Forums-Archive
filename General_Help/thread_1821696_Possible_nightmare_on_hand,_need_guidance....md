---
title: "Possible nightmare on hand, need guidance..."
date: 2011-08-09
forum: General Help
---

### Post by zero2xiii on 2011-08-09
Hay all,

Due to the lack of consumer choice offered by software developers, I need to install windows 7 on a notebook already containing 2 ubuntu distros:
1. Ubuntu 11.04_64
2. Ubuntu studio 10.04_64

Now here comes the tricky part. My harddrive is already almost 90% full (500GB drive). So I cant install windows alongside the already installed ubuntus.

I now consider the following two options:
(The laptop has an eSATAp port)

1. "Clone" or otherwise move the current HDD content to an external HDD connected via eSATA and boot ubuntu from there (keeping my grub and all that intact) or,

2. Install windows 7 to the external drive and using the boot menu (F12) to select that drive as my boot device.

I prefere option 2, as this drive wont be connected to other computers, windows shouldn't shoot me for "changed hardware" each time. As it is SATA in effect, I assume the speed of the system will be faster compared to USB 2.0?

Is any of this at all possible? I have a 1TB external drive (USB 2.0), but I will be buying a sata to esata/usb enclosure tomorow.


Has anyone ever attempted anything like this? Is my assumption of the eSATA vs USB 2.0 correct?

Thanks in advanced :)

---

### Post by dcollier on 2011-08-09
Why don't you install virtual-box and run windows from within ubuntu-

---

### Post by blind2314 on 2011-08-09
> **zero2xiii said:**
> Hay all,

Is any of this at all possible? I have a 1TB external drive (USB 2.0), but I will be buying a sata to esata/usb enclosure tomorow.


Has anyone ever attempted anything like this? Is my assumption of the eSATA vs USB 2.0 correct?

Thanks in advanced :)

If your enclosure still uses USB at some point in the transfer, all your speed gains from SATA are lost. The connection is only as fast as its weakest/slowest point.

If you plan on removing the drive and connecting it via its SATA connection to an eSATA enclosure, then yes, you will see a speed gain.

---

### Post by zero2xiii on 2011-08-09
> Why don't you install virtual-box and run windows from within ubuntu-

[http://ubuntuforums.org/showthread.php?t=1817635](http://ubuntuforums.org/showthread.php?t=1817635)

---

### Post by zero2xiii on 2011-08-09
> If your enclosure still uses USB at some point in the transfer, all your speed gains from SATA are lost. The connection is only as fast as its weakest/slowest point.

The enclosure I have in mind (cooler master xport 351) has a USB and eSATA port? So I assume it supports both, seperately (eg nowhere is is just an interface from one to the other)

---

### Post by Mark Phelps on 2011-08-09
> **zero2xiii said:**
> I prefere option 2, as this drive wont be connected to other computers, windows shouldn't shoot me for "changed hardware" each time. 

This option is not available.  Win7 won't support being installed to removable media.  There were "hacks" that made this possible with XP, but those won't work with Win7.

---

### Post by zero2xiii on 2011-08-09
> This option is not available. Win7 won't support being installed to removable media. There were "hacks" that made this possible with XP, but those won't work with Win7.

yep I have heard about those "hacks" as you call them.. But I'm hoping that attaching the drive via eSATA will allow that. Since it is picked up (according to online sources) in the same fashion as a internal SATA drive..

---

### Post by blind2314 on 2011-08-09
> **zero2xiii said:**
> yep I have heard about those "hacks" as you call them.. But I'm hoping that attaching the drive via eSATA will allow that. Since it is picked up (according to online sources) in the same fashion as a internal SATA drive..

That entirely depends. It uses a different controller from the "actual" SATA connections on the board, and it's entirely possible that this controller will report the drive differently. You can try and see, worst case scenario windows setup just won't let you continue.

---

### Post by Blasphemist on 2011-08-09
Just curious before you go through all of this, what software is it that is forcing you to do this?

---

### Post by zero2xiii on 2011-08-10
> Just curious before you go through all of this, what software is it that is forcing you to do this?

hmm as linked earlier:
[http://ubuntuforums.org/showthread.php?t=1817635](http://ubuntuforums.org/showthread.php?t=1817635)

But to sum it up:
Cubase
Protools
Final cut pro X
Adobe multimedia suite (I think its called...)
and MIDI controlers working with above mentioned programs.

Its for a course I need to do in sound engineering and video post production.

---

### Post by zero2xiii on 2011-08-20
Hay all,

Just to report back on my testing:

Installing windows 7 to an eSATA 3.5" drive worked :D
It has virtualy zero performance loss compared to internal drives (although the laptop's internal drive is 5700 RPM and the external is 7200 RMP)

I removed my internal drive and installed windows to the external drive, now I just use F12 to open up the boot device selection screen and select the external drive if I wish to boot windows.

The ONLY problem I have been experiencing is that linux does NOT mount the eSATA device if it is connected after power-up (eg hot-swaped). This is not a MAJOR problem, but sometimes it can be hasseling.

Well thats it, thanks for all the input :)

---

