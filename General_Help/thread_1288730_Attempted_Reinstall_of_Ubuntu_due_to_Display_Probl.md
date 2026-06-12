---
title: "Attempted Reinstall of Ubuntu due to Display Problems"
date: 2009-10-11
forum: General Help
---

### Post by Warmwind76 on 2009-10-11
System details first...

Biostar TA790GX 128M motherboard
Graphics: Integrated ATI Radeon HD 3300 with HDMI/DVI and VGA out
Chip: AMD Athlon 64X2 dual core 4200, 2.2 GHz
RAM: 4 GB
1st hard drive: HDT with 230 GB storage with Windows XP SP3
2nd hard drive: WDC with 320 GB storage with Ubuntu 9.04
Two monitors: HP 22-inch pivot and Gateway 21-inch pivot

Successfully installed Ubuntu independently on the 2nd hard drive with the 1st XP hard drive disconnected.

Ubuntu was running fine, but there were some display problems with the two monitor setup.  Attempted to resolve these problems using the Display Manager: identify monitors, turn off mirroring, etc. Eventually, the Display Manager would cease to respond, simply freezing. Using the System Monitor, one CPU was running full tilt at 100%, then it would go to almost 0% resources being consumed, and would switch over to the other CPU, which then registered 100% resources being consumed. Had to shut  down and went through the whole process again (and again...). Same results.

Per suggestions from this forum, at boot, used the xfix option to repair the graphics. This really horked things up. Ubuntu would start to boot, then the display would only show a weird, tiled screen across the top of both displays, a series of very small images that may have been the Ubuntu start up or the bios set up. Couldn't tell. Attempted Recovery several times to no avail.

Okay, my Windows OS is intact being on a separate drive, so I'll start from the top and reinstall Ubuntu on the second hard drive. I brought the second drive down to where I started, that is, unallocated, removed the partitions created by Ubuntu at first load. Attempted to reinstall Ubuntu from DVD using Boot From DVD Drive from the boot menu as before.

GRUB 1.5 indicated startup, then it would stop with an Error 22. 

I guess my assumptions were wrong about removing the partitions, assuming that the OS install would prompt to reestablish the partition and then the install would know where to install the GRUB.

So I'm at a complete loss as to how to proceed.

I certainly don't want to re-experience the display problems that got me into this mess in the first place.

At least I still have Windows XP running on the first drive, so I'm not ready to slit my wrists yet in frustration.

Thanks in advance for any assistance.

---

### Post by Warmwind76 on 2009-10-14
What? Too complicated?

---

