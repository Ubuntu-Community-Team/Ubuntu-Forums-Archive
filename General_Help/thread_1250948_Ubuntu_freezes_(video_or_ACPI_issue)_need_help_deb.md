---
title: "Ubuntu freezes (video or ACPI issue?): need help debugging the problem"
date: 2009-08-27
forum: General Help
---

### Post by yankeeDDL on 2009-08-27
Hello,

I'm building a new PC and I'm having some problems that I haven't been able to debug.
First of all, the hardware:
Athlon II X2 240
Biostar GF8100 M2+ (integrated Nvidia GeForce 8100, up to 512MB of shared mem)
4GB of DDR2
I'm installing Ubuntu x64.

The install goes ok. No problem. The PC boots and works fine, but on the VGA driver. I get notified that I can use restricted HW driver for the video card.
First I install all the upgrades, then reboot (the new Kernel is there) and only then I enable the graphic drivers.
I reboot and the screen goes to a more reasonable resolution (1024x768).
At this point the PC operates fine: I have installed and can use Skype, I tried multiple pre-installed software (openoffice, firefox ...) and they all work fine.
But if I try to access the power management menu (for example to set the timeout for shutting down the monitor) the PC freezes. Sometimes I can still see the mouse moving, but most of the time the screen is partially corrupted and all I can do is a physical reset.
I noticed that changing the resolution to 1152×864 makes the crash a bit more likely, but I can hardly quantify that.

I think it's either a problem with the video driver, or with the 
power management. I don't know how to go about debugging ... or fixing it.

I downloaded the latest Nvidia driver (Ubuntu installs the rev 180: on th website there's rev 185), but to install it I need to kill X and I haven't been able to do so (I so Ctrl+Alt+F1), I find the PID for X:0 and kill it, but all it does is bring me back to Gnome ...

Note: I also have a discrete video card (Ati HD2600) but I'd rather not use it since it gets really hot and I don't really plan on playing games or other 3D-intensive stuff on this PC, so I'd rather stick to the on-board GeForce 8100.

Any suggestions on how to deal with this would be appreciated. 

Thanks.

---

### Post by P4man on 2009-08-27
can you attach or post (wrapped in code tags pls :) ) the output of dmesg ?

---

### Post by P4man on 2009-08-27
also check in system > administration > log file viewer

if you find any errors that happen at the time you get those freezes.

---

### Post by yankeeDDL on 2009-08-27
Hi,

I attached the dmesg.
Not sure if it's really helpful though: this is the file I can see after rebooting (when the system freezes ... well, it's frozen so I can't see dmesg ...).

Thanks for the help: let me know if you see anything wrong with it.

Thanks again ...

---

### Post by P4man on 2009-08-27
the log file viewer lets you see the log history, so you can "scroll back" to the point where it froze up. Since you can trigger it easily by just opening energy settings, I suggest you try that.

---

### Post by yankeeDDL on 2009-08-27
Thanks P4man. I'll try that.
I'll also try to install the latest Nvidia drivers (185).

---

