---
title: "usb problems with ubuntu and other linux"
date: 2011-01-09
forum: General Help
---

### Post by dci on 2011-01-09
I created a bootable usb drive in ubuntu 10.10, but when I boot from it, it just stays on the loading screen forever. My laptop boots up fine using the same flash drive. 

The same thing happens with a bootable usb drive that I created with nimblex. It works fine on my laptop, but when I try to boot from it on the desktop, I get "waiting for slow usb devices. . . . . fatal error" etc and it fails. 

Usb devices work fine in ubuntu once its booted up either via cd or hard drive, and also works fine in windows. They don't work in nimblex though.

I looked in my BIOS and didn't see any obvious problems, but I don't have any experience with this.

---

### Post by dci on 2011-01-09
the motherboad is gigabyte ma785gm-us2h with amd athlon 64

this is similar hardware to the person in this thread that also had usb issues

[http://ubuntuforums.org/showthread.php?t=1657763&highlight=usb](http://ubuntuforums.org/showthread.php?t=1657763&highlight=usb)

his devices didn't work at all though, and i'm not exactly clear on what the solution was.

---

### Post by C.S.Cameron on 2011-01-09
How old is the computer?

---

### Post by dci on 2011-01-09
a little over a year, and the motherboard i got just a few months ago.

---

### Post by dci on 2011-01-09
I got it working now. It was because I had a floppy drive listed in my bios and none installed.

---

