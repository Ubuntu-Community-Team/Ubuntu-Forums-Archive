---
title: "graphical console going blank"
date: 2006-03-19
forum: General Help
---

### Post by slightly72 on 2006-03-19
Hi,

When switching to a text console (with ctrl+alt+f1), and then switching back to the graphical console (ctrl+alt+f7), the screen goes blank -- can't do anything but reboot the laptop. I also cannot switch to the text console at this point. I think this problem also shows up when hibernating the laptop: upon resuming it, the disk image seems to load correctly, but when trying to initialize the graphical mode the screen is blank. My feeling is that the laptop has resumed correctly, since it shutdowns when keeping the power button pressed.

My card is (from lspci):

> 0000:00:02.0 VGA compatible controller: Intel Corp. 82830 CGC [Chipset Graphics Controller] (rev 04)
0000:00:02.1 Display controller: Intel Corp. 82830 CGC [Chipset Graphics Controller]

The card uses shared memory, the "agpart" kernel module is loaded. This is the device section from the xorg.conf file:

> Section "Device"
        Identifier      "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        49152
EndSection


I've added the VideoRam line, based on the Windows settings.

Any suggestions on solving this problem are really appreciated. Also, let me know if you need any more information about the laptop setup.

---

### Post by jerrykenny on 2006-03-19
Have you possibly enabled the function within the screensaver to "lock the screen" and prompt for a password after so many minutes of idle . . . 

It may be a power saving thing . . . . the screen has just been completely switched off ( maybe it thinks no GUI=no more work for me today=night night)

?

---

### Post by slightly72 on 2006-03-20
Thanks for the tip. I've disabled power management in the screensaver. However, I think the problem was addressed in this post: [http://www.ubuntuforums.org/showthread.php?t=88030]("http://www.ubuntuforums.org/showthread.php?t=88030") it seems to work for both switching to text consoles and back, and for hibernate. There's only one more problem with the laptop now, random system crashes, will have to continue digging.

---

