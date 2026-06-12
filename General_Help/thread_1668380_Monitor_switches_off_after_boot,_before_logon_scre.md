---
title: "Monitor switches off after boot, before logon screen"
date: 2011-01-16
forum: General Help
---

### Post by random user name on 2011-01-16
hello all,

I had a good look at this article I found using google

[http://ubuntuforums.org/showthread.php?t=1646307&highlight=monitor+turns](http://ubuntuforums.org/showthread.php?t=1646307&highlight=monitor+turns)

but it doesn't quite match my situation. what I'm experiencing is:

1. I can run the graphical installer at full resolution without using "nomodeset"
2. I can boot into the Gnome desktop using the option "Try without installing" without any problems
3. When I install to my HDD however, I can boot but just at the point where the logon screen should come (after the black screen, blinking cursor), the display reports no signal and goes to sleep. I can hit enter, type my password, hit enter again (blind, as there's no display) and the HDD spins up as if logging in, but I don't see anything.
4. Using "nomodeset" makes no difference whatsoever other than the graphical installer runs at a lower res.
5. using the alternate installer changes nothing
6. recovery mode has the same issues

It appears to me that booting into Gnome without installing uses some sort of generic driver, whereas installing uses a different driver which is sending my display to sleep. 

I'm using Ubuntu 10.10 64Bit. Have also tried using 10.04 64Bit and the alternate 10.10 .iso, but to no avail. My graphics card is an NVidia Quadro NVS 295 with a DisplayPort-DVI adapter. I've previously installed 10.04 64Bit on another system with an NVidia GT240 card with no problems whatsoever. I can't try that card in this machine as it's too big for the case chassis, let alone the case.

any help with this is greatly appreciated.

---

### Post by lithopsian on 2011-01-16
Your installation is presumably not using suitable drivers for your graphics card.  This is your chance to learn the Linux command line :)

Or you can boot to a failsafe session which will use only the most basic graphics that should work with almost any card and a generic driver.  Should be an option for you on the Grub menu.

If you can get that far then you can check if you have the driver for your card installed and whether it is being used.  You can run lspci and check /var/log/Xorg.0.log to see if your card is being correctly recognised, then try to install the correct driver for it.  If the correct driver is already installed then you might need to run run nvidia-settings to configure it properly.

---

### Post by random user name on 2011-01-16
lithopsian, I think you're quite correct in your assumption that my install is not using suitable drivers.

How do I get to the command line?

I tried ctrl + alt + F1 to try and get to tty1, but the monitor remains asleep.

how do I boot to a failsafe session? I guess this isn't recovery mode?

---

### Post by random user name on 2011-01-16
Panic over.

Using this post [http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset](http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset) I was able to configure GRUB to boot the installed OS with "nomodeset" which as I suspected would at least get me into the desktop, then I was able to install the correct driver just using GNOME. sweet. I incorrectly assumed that running the installer with "nomodeset" would configure GRUB to match. my bad.

---

