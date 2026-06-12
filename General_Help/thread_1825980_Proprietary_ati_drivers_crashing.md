---
title: "Proprietary ati drivers crashing"
date: 2011-08-16
forum: General Help
---

### Post by vanquishedangel on 2011-08-16
Hi again and I hope this post helps both developers and users.

I first tried mesa and I love mesa but I am buying a new ati radeon hd 6450. Mesa has ability in it to run the card in 7.11 but here is the issue.

I am running Lubuntu 11.04 64 bit on a dc7100sff with an ati radeon hd 4350 and decided to upgrade mesa through xorg edgers early, before the new card arrived.  I play neverwinter nights 1 through playonlinux and wine, I also play perfect world international the same way.  To my surprise the xorg drivers from edgers failed, both games the loader started but then just quit after the loader was done. So I tried the "Additional Drivers", diver manager and it played neverwinter well but would only play perfectworld in playonlinux for about 5 mins, Then the whole operating system would freeze.  I had to do a hard reboot.  So I downloaded the ati drivers from ati's website and ran the .run file, all seemed well until I opened playonlinux and a warning came up about installing 3d acceleration, neither game worked. I tried dev files for mesa with just mesa, I tried hardware manager/driver manager, and the drivers from ati website, the only ones that worked was the original mesa in natty (7.10), and the ones from x-swat, and the devs (mesa 7.10).

I also followed the guide under "Install the fglrx Driver from AMD/ATI Catalyst 11.2 For Ubuntu 10.10 Maverick" on this page here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) This one gave an error something about parse line 2 in /etc/X11/xorg.conf ( i changed 11.2 to 11.7 and put natty in place of maverick where needed)

After much searching I found a post on ubuntu.fr.org that I couldn't understand but had an Idea. They posted the contence of their xorg.conf so I copied and pasted part of it to mine,also it is in my xorg.conf.fglrx-0 here is the contence:

Section "Module"
	Load    "i2c"
	Load    "bitmap"
	Load    "ddc"
	Load    "dri"
	Load    "extmod"
	Load    "freetype"
	Load    "glx"
	Load    "int10"
	Load    "type1"
	Load    "vbe"
	Load    "dbe"
EndSection

This worked with the install from the guide posted above. I tried Load dbe and load dri both by themselves and that didn't work, but with the whole thing in my xorg.conf the games both work with ati proprietary drivers.

Since the crashes were the same in both proprietary drivers (the ones from the driver manager and the ones from ati's site that I chaged in the guide not the .run) I ran the "Additional drivers" again and it said something about a different version in use, I clicked activate anyway to get the drivers that are provided through Ubuntu and this worked.

In short for people trying to fix this problem, install the drivers from "additional drivers" and then copy and paste this in /etc/X11/xorg.conf and xorg.conf.fglrx-0  then reboot.

For ubuntu people or other devs, the problem isn't with wine or playonlinux and one or all of those entries in the xorg.conf should tell you the issue with the ati drivers.

As for the mesa (7.11) not working I am not sure what the problem is, maybe it is the same issue but I have no clue. Hope this helps.

---

### Post by vanquishedangel on 2011-08-18
I have fixed the issue and to cut along story short after trying every thing under the sun I can think of, here is what I have found.

1.If you need to install ati proprietary drivers in ubuntu 11.04 natty (in my case Lubuntu) do so from booting in safe graphics mode and running "additional drivers" in the menu (boot into safe mode by holding shift as it boots and select the safe mode or recovery kernel) This has solved the libso error after running sudo aticonfig --initial

2. playonlinux/wine doesn't deem to play nice in perfect world with multisampling enabled also on the perfect world bootloader select graphics and turn them all low, select windowed mode, and run the resolution at 800x600 (the fixes here maybe card specific because the 4350 is low end)

3. I no longer need any of the above settings in the post above this one, it works as is with no meddling.

---

