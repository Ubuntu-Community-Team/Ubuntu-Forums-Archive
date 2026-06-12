---
title: "How do I install Hardy from a USB flash drive?"
date: 2009-12-18
forum: General Help
---

### Post by YosefKaro on 2009-12-18
Alright Hardy Gurus, I've been googling this for the past 3 or 4 hours and only running into dead ends.  After trying out ubuntu for a few months I've decided that I would really like to give Hardy a go but I'm stumped.  I don't have any cd's available to burn the ISO, just a USB thumb drive.  However, in the course of the Hardy installation, one of the steps is to mount the cdrom :(  It is at this point that my install gets borked.  There seems to be no way to circumvent this requirement.  The install starts out just fine from the USB then it hits this dead end.  Anyway around it?

-Yos

---

### Post by todak on 2009-12-18
This should help you: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by YosefKaro on 2009-12-18
Thank you but that is one of the things that I have been trying ie UNetbootin.  I run into the same wall with it: it reaches a point where it wants to mount a cdrom to continue.  For some reason, it just won't continue the install from the USB itself :(

-Yos

Oh, and the option for it to download and install from the internet will not work for me because I use a broadband dongle that has to be tweeked to work.

---

### Post by todak on 2009-12-18
Hmm...have you tried using the alternate, i.e., text-based install image rather than the live image?

---

### Post by YosefKaro on 2009-12-18
text-based install image?  That's new to me so no, I haven't tried that method.  How do I do that?

-Yos

After googling that, that appears to be the method that I have been using; my ISO doesn't even have a live cd option from the usb.

---

### Post by todak on 2009-12-18
Apparently it is a bug. [This]("http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/") page explains how to get it to work properly. See [here]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192") for an explanation of the bug. Read [this]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Preparing%20the%20USB%20drive")also for more information.

---

