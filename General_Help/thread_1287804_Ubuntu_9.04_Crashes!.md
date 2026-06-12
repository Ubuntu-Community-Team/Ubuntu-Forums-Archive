---
title: "Ubuntu 9.04 Crashes!"
date: 2009-10-10
forum: General Help
---

### Post by Snackmafia on 2009-10-10
Hello!  I just installed Ubuntu and everything was going great.  I installed Compiz and enabled the "thumbnail" thing where you can mouse over a window and it shows you a little preview.  Suddenly, the screen turned black (in stages).  I did a forced reboot, and the same thing happened.  I uninstalled, then reinstalled, only to have the same problem again.  I realize that this only happens after I install Compiz, but if I can't get Compiz, I don't really want to use Ubuntu that much.  Please help!

---

### Post by Woody1987 on 2009-10-10
graphics card and driver?

---

### Post by andy16666 on 2009-10-10
Can you give some information on what make your graphics card is and whether or not you are using the restricted drivers? Some graphics cards (for example many ATI cards) have certain vendor imposed limitations on Linux. (i.e.: the drivers for those cards are somewhat neglected). An NVidia or Intel graphics chips is highly recommended for compiz.

If you have an NVidia (or ATI) video card make sure you visit System->Administration->Hardware Drivers and select the latest version of the NVidia driver.

---

### Post by Guy Sibley on 2009-10-10
I have had crashes in Jaunty which are more akin to the MAC rainbow wheel of doom where everything just freezes including force quit and the option to shut down, which means cold power off. Any solutions or is this caused by me doing something dumb?

---

### Post by Guy Sibley on 2009-10-10
@snackmafia Compiz is cool and all, but Ubuntu has lots to offer (for free) aside from that! work your problem out and it will work, even if it doesn't stick with it and hopefully you will see like I did that it is a really cool OS.

---

### Post by Snackmafia on 2009-10-10
Hey thanks for all of your help!  Here is all of the information i could find on my graphics card:


Intel(R) Graphics Media Accelerator Driver Report


Report Date:		10/10/2009
Report Time[hr:mm:ss]:	22:50:30
Driver Version:		6.14.10.4764
Operating System:		Windows XP* Home Edition, Service Pack 3 (5.1.2600)
Default Language:		English
DirectX* Version:		9.0
Physical Memory:		501 MB
Minimum Graphics Memory:	8 MB
Maximum Graphics Memory:	128 MB
Graphics Memory in Use:	9 MB
Processor:		x86
Processor Speed:		3333 MHZ
Vendor ID:		8086
Device ID:		2582
Device Revision:		04


*   Accelerator Information   *

Accelerator in Use:		Intel(R) 82915G/GV/910GL Express Chipset Family
Video BIOS:		1295
Current Graphics Mode:	1024 by 768 True Color (60 Hz)



*   Devices Connected to the Graphics Accelerator   *


Active Monitors: 1


*   Monitor   *

Monitor Name:		Plug and Play Monitor
Display Type:		Analog
Gamma Value:		2.29
DDC2 Protocol:		Supported
Maximum Image Size:	Horizontal: 11.0  inches
			Vertical:   9.0  inches
Monitor Supported Modes:
640 by 480 (60 Hz)
640 by 480 (67 Hz)
640 by 480 (72 Hz)
640 by 480 (75 Hz)
720 by 400 (70 Hz)
800 by 600 (56 Hz)
800 by 600 (60 Hz)
800 by 600 (72 Hz)
800 by 600 (75 Hz)
832 by 624 (75 Hz)
1024 by 768 (60 Hz)
1024 by 768 (70 Hz)
1024 by 768 (75 Hz)
Display Power Management Support:
	Standby Mode:	Not Supported
	Suspend Mode:	Not Supported
	Active Off Mode: Supported






  As for the restricted drivers, I have not installed any of those.  Since my first post, I did another uninstall-reinstall of Ubuntu and the same thing happened.  I think it has something to do with Compiz.  And for guy sibley I know Ubuntu has a lot more to offer than just to look good, it's just one of the main things I want the most.  Once again, thanks everyone!

EDIT: I installed using Wubi if that makes a difference

---

### Post by clhsharky on 2009-10-10
Hi Snackmafia

try raising Graphics Memory in bios' 9MB seams very low.
Compiz likes memory.

---

### Post by Snackmafia on 2009-10-11
sorry how do I do that?  And I can't even do anything unless I do a reinstall because it happens almost immediately.

---

### Post by Snackmafia on 2009-10-11
Also I've thought of using Kubuntu or Xubuntu.  Would this help?

9.04 is the first update where I've had Wi-Fi work in Ubuntu.

---

