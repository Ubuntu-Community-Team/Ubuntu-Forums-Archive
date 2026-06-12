---
title: "Sleep, hibernate and special effects do not work"
date: 2010-05-21
forum: General Help
---

### Post by jamesa00789 on 2010-05-21
Dear all,

I have recently switched to Ubuntu from Windows Vista. But I am having a few problems, any pointers will be grand.

First sleep and hibernate do not work. My laptop sleeps or hibernates fine, but on awake I just get a blank screen and the hard drive doesn't spin at all. This also disables the network manager, which is a real pain.

Also for some reason I can't enable special effects. I have the ATI Radeon 200M series integrated graphics chipset.

Thanks!



Heres some spec details:

```
Summary
Computer
Processor	2x Genuine Intel(R) CPU T2060 @ 1.60GHz
Memory	895MB (353MB used)
Operating System	Ubuntu 10.04 LTS
User Name	James (James)
Date/Time	Fri 21 May 2010 20:15:41 BST
Display
Resolution	1280x800 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA ATI SB
Input Devices
Lid Switch	
Power Button	
Power Button	
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Video Bus	
HDA Digital PCBeep	
SynPS/2 Synaptics TouchPad	
Printers
No printers found	
SCSI Disks
Optiarc DVD RW AD-5540A	
ATA ST980811AS	
Lexar JD FireFly	
Operating System
Version
Kernel	Linux 2.6.32-22-generic (i686)
Compiled	#33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010
C Library	GNU C Library version 2.11.1 (stable)
Default C Compiler	GNU C Compiler version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
Distribution	Ubuntu 10.04 LTS
Current Session
Computer Name	James-Laptop
User Name	James (James)
Home Directory	/home/james
Desktop Environment	GNOME 2.30.0
Misc
Uptime	40 minutes
Load Average	1.56, 1.11, 0.88
```

---

### Post by cain071546 on 2010-05-21
dont know about the sleep or hibernate but with the effects, Are You using a proprietary driver?

---

### Post by jamesa00789 on 2010-05-21
> **cain071546 said:**
> dont know about the sleep or hibernate but with the effects, Are You using a proprietary driver?

I think I am using the X.org AMD/ATI display driver, how do I find this out? I have tried installing the driver from the ATI website, but I can't remember if it worked.

---

### Post by cain071546 on 2010-05-21
go to system/administration/hardware drivers tell me what it says

---

### Post by jamesa00789 on 2010-05-21
> **cain071546 said:**
> go to system/administration/hardware drivers tell me what it says

After searching for drivers it just says "No propriety drivers are in use for this system"

---

### Post by cain071546 on 2010-05-21
try installing the proprietary drivers then post back with results

---

### Post by cain071546 on 2010-05-21
did you find a solution?

---

### Post by jamesa00789 on 2010-05-23
Hey,

No I don't know how to install the drivers for Linux. I have downloaded the driver from the ati website, so how do I install it? It doesn't seem to be as simple as windows.

Cheers

---

### Post by warfacegod on 2010-05-23
Before you go any farther with that go to: 

System> Admin.> Software Sources> Ubuntu Software tab> make certain there is a check next to the top four options> 

Other Software tab> make certain there is a check next to "http:.....ubuntu lucid partner (should be the top of the list)> 

Updates tab> put a check next to Unsupported updates (lucid-backports)

Now click Close. It will ask you to Reload which you should do. Then go to:

System> Admin.> Update Manager (this may open automatically after you've clicked Reload)> and install all updates.

Now check Hardware Drivers again to see if anything is there. If so, install the (Recommended) driver.

I know read this it seems like allot to deal with but it really isn't.

---

### Post by jamesa00789 on 2010-05-24
Heya buddy,

I have done all of that and still no Radeon drivers to install. I assume you mean System > Administration > Hardware drivers yep?

Thanks for your help anyway. How do I install the Radeon driver the old fashioned way? I have downloaded a .run file off their website. Still getting used to linux.

Also, got any tips how I can get my sleep and hibernate to work?

Thanks

---

### Post by warfacegod on 2010-05-24
> **jamesa00789 said:**
> Heya buddy,

I have done all of that and still no Radeon drivers to install. I assume you mean System > Administration > Hardware drivers yep?

Thanks for your help anyway. How do I install the Radeon driver the old fashioned way? I have downloaded a .run file off their website. Still getting used to linux.

Also, got any tips how I can get my sleep and hibernate to work?

Thanks

Can't help you with the ATi .run

I don't use Suspend/Hibernate but I do know that your swap must be at least slightly bigger than your RAM.

Sorry I can't be more help at the moment.

---

