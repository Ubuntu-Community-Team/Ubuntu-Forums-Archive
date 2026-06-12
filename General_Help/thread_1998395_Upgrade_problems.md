---
title: "Upgrade problems"
date: 2012-06-06
forum: General Help
---

### Post by wrknight on 2012-06-06
Is there any way to upgrade to 12.04 without first upgrading to 11.10.  I have tried upgrading to 11.10 three times, each with disastrous results that forced me to go back to 11.04.  This last time I completely lost control of my computer.  I can't even log out or switch user.  I can shut down the machine only by holding down the power switch.  I have no menu bar, no desktop controls and no configuration controls.  There is no bottom panel with anything, no side panels and the top panel has only "file", "edit", "view" "go" "bookmarks" and "help" (and the latter doesn't help).

I have never seen anything like this and I have no idea what to do except to start all over with a new install.

PS  Is there anyway to go backward to 11.04 without reinstalling from a disc?

---

### Post by ajgreeny on 2012-06-06
Does 11.10 or 12.04 live CD/USB work on your machine?

If neither will run properly it may simply be that the computer is not capable of running unity and/or the gnome 3, gtk+ 3 versions of everything that both 11.10 and 12.04 use.

---

### Post by wrknight on 2012-06-06
That's not a lot of help.  I'm not ready to accept having to buy a new computer just to upgrade Ubuntu.  This computer is less than two years old, has a dual core pentium cpu, has lots of hard drive and RAM and should be able to take on any current operating system.

---

### Post by ajgreeny on 2012-06-06
Yes, if it's only two years old, I agree, but the thing you didn't mention is the graphic card.  I think there are problems with some of the proprietary drivers in 12.04 and to some extent in 11.10, but as I don't need any of them on my old ATI card, I can't help you with any more detail.

Find what card you have with ```
lapci
``` or ```
sudo lshw -c display
```and search out any known difficulties with that in this forum and generally in [www.googlubuntu.com](www.googlubuntu.com).

Sorry I can't help you more, but you note I am still using 10.04 as my main OS with test partitions of Lubuntu, Xubuntu and Ubuntu 12.04 (classic desktop) just to have as good look before I jump to one of those.

---

### Post by Kr0nZ on 2012-06-06
> **wrknight said:**
> That's not a lot of help.  I'm not ready to accept having to buy a new computer just to upgrade Ubuntu.  This computer is less than two years old, has a dual core pentium cpu, has lots of hard drive and RAM and should be able to take on any current operating system.

so will it even boot the live cd/usb?

---

### Post by LiamOS on 2012-06-06
If you're able to rescue everything after a dodgy upgrade attempt, you could try it again, and if(When) it goes bad, turn off the computer and boot from a live CD/USB (I'd recommend Gentoo's minimal install image if you're comfortable in a command line). 
With that done, you can mount your partitions(And maybe chroot into your system) and have a poke around to see what stage the update is at, etc. If you're lucky, you'll only have boot problems, which shouldn't be terribly difficult to sort out with some help from the Grub2 help pages. If you're unlucky, you'll have no working kernel or something similar. If that's the case, I don't know how you'd proceed.
If you're comfortable doing it, mounting everything and looking around would be a very good way to figure out what's actually happened during the upgrade attempt.

---

### Post by wrknight on 2012-06-06
Right now, it's too late to try that.  After a couple of fruitless attempts to fix gnome and a couple of reboots, the update manager popped up and asked if I wanted to upgrade to 12.04.  I said yes and it is doing so as we speak.  We shall see what happens.

It seems to be taking longer to upgrade than it did to do a fresh install of 11.04.  I don't know if that's normal or what.

---

### Post by wrknight on 2012-06-07
Ok, 12.04 installed and appears to be running. I can't find a "systems" menu drop down in the menu panel, but maybe that's intentional.  I can't unlock the top panel to adjust the position of the launchers or move the panel to a different location on the display.  Also, the control center has only a fraction of the controls that the old one had.

There are substantial delays during boot up. I get two messages, one after the other causing delays in booting up.

1 Disc drive not ready   (waits for about 1 minute)
2 Waiting for network    (waits for two more minutes)

A third message tells me it's booting without full network and that ends the delays

Altogether it's taking about 4 minutes to boot up.

Any help I can get on those problems will be appreciated.

---

