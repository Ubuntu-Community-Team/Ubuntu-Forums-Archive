---
title: "Cant Install Ubuntu?"
date: 2012-01-06
forum: General Help
---

### Post by hxcfelony on 2012-01-06
Hello I have installed Ubuntu on my old computer in the past so installation is not a problem for me. The problem is, no matter what I use (USB, DVD, Wubi) I get to the point on the screen where it says Ubuntu, then it will go pixelated and wont continue. This is strange since I can install Debian or OpenSuse but not Ubuntu. Specs are:
Intel Core 2 Duo E7600
4 Gigs of Ram DDR2
Nvidia Geforce GT 240 (Im using DVI not HDMI)
Motherboard Bios is updated (3/11/2011)
Also for the record I use 64-bit operating systems, so I tryed the 64-bit version of Ubuntu, dont really know what Wubi trys to install but the results are the same. I will post more information if needed. Thanks!

---

### Post by grahammechanical on 2012-01-06
This thread may help you:

[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

I am guessing that you need the Nvidia driver installed but as it can only be installed after Ubuntu has been installed and booted you need to change something at the Grub boot time to load Ubuntu with a basic video setting and then install the Nvidia driver. This is my guess.

I am using the Nvidia Geforce GT 220. And there are drivers for it. So, you will be able to get things working through Additional drivers once you get past this problem.

See that link. Look for something about boot with nomodeset. This, I think might solve it. It stops the boot process from trying to set a video mode. And so will boot with a standard video mode that should get you to a working desktop where you can install the Nvidia driver.

Regards.

Regards.

---

### Post by topsites on 2012-01-06
Yes, I can almost guarantee it's got to do with that <snip> <snip> Nvidia <snip>.

---

### Post by Rubi1200 on 2012-01-07
You can try using the option to set nomodeset that grahammechanical linked to above.

---

