---
title: "early failure to install from CD"
date: 2011-04-05
forum: General Help
---

### Post by roe46 on 2011-04-05
Hi
everybody is going for ubuntu, so I decided to give it a try. I downloaded ubuntu for desktop and created an usb-stick. I am using an old hp eVectra PC as an "guinea-pig". I configured its bios to use usb as first boot device. It did not boot from there, but went straight on to the debian on the HD.
Ok, let's go for a CD. I burnt the image and tried again. It recognized the CD, but it reported:
Code:
graphics initialisation failed
Error setting up gfxboot
boot:
and repeated this endlessly.
Meanwhile, I used this CD on an other PC - but not for an installation, but only for a trial run. It worked, hence the CD seems to be ok. Any ideas around what I should try next? 
Thanks and regards roe46

---

### Post by sanderj on 2011-04-05
How old is the hp eVectra PC? Older PCs don't boot from an USB stick.

How much RAM has it got? [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) says you need at leat 512 MB RAM.


If you're below that, you could try Xubuntu or Bodhi Linux (both Ubuntu based)

Regarding the error message: [http://ubuntuforums.org/showthread.php?t=1594003](http://ubuntuforums.org/showthread.php?t=1594003) says you should type "help" on the command prompt.

---

### Post by roe46 on 2011-04-05
Yea, its an old machine:
e-Vectra with Pentium III, i810E chipset 256 MB RAM running at 667EB Hz (419819 Hz). I thought that is enough just to learn how to install ubuntu. Currently a have debian installed. Is ubuntu so much more RAM-hungry? Anyway, I typed help and got a nice help screen. But this then is the end. The system does not react on any of the (recommended) key strokes F2...F10 or enter.

---

### Post by sanderj on 2011-04-05
Ubuntu is more memory-hungry because it does a grahical install.

You could try Xubuntu, or Bodhi Linux, or Ubuntu Server (which has a non-GUI install).

---

### Post by roe46 on 2011-04-05
Meanwhile I have downloaded debian-6.0 netinst.iso. This works, I am guided through menues etc. But I canceled the installtion, once it started to download packets, because this slowed dramatically down my concurently (on an other PC) running download of xbuntu.

When booting from the xbunto 10.10 CD, it produces the same error as before. Entering help then produces the same screen, but this time it seemed to react. It switched to a screen with only xbuntu 10.10 and 4 dots that alternatively lighted up. Then I pressed other key, because I got the impression, the system hangs....but suddenly it continued and started listing a log. The message "checking battery" was one of the last things I saw before the screen went completely black. And stayed so for several minutes. But again - suddenly it woke up again and now it displays a nice graphical xbuntu 10.10 screen with some nice icons. Is all this - and expecially the long dark periods, normal?

---

### Post by nothingspecial on 2011-04-05
Your problem is that you are trying to do a graphical install with 256M RAM.

Download the minimal iso and do a text install, then during the tasksel process select xubuntu-desktop or ubuntu-desktop.

---

### Post by roe46 on 2011-04-05
The minimal iso - is that whats termed "alternate iso" in e. g. [ftp.tu-chemnitz.de/pub/linux/ubuntu-cdimage/xubuntu/releases/maverick/release/]("ftp.tu-chemnitz.de/pub/linux/ubuntu-cdimage/xubuntu/releases/maverick/release/")

Let me add that the nice screen I mentioned previously is nice only, but nothing works. As an example: Clicking on the Firefox icon brings up a "busy" symbol, but it disapears after a few seconds and nothing happens. I have the impression the system runs from CD only and does not touch the HD.

Ok, I will give it another try with the alternate CD - if indeed this is the minimal iso you were talking about.

---

### Post by nothingspecial on 2011-04-05
I was actually talking about this

[http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/mini.iso)

---

