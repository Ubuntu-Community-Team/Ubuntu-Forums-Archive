---
title: "Cannot get the proper screen resolution with Hoary Live CD"
date: 2005-02-18
forum: General Help
---

### Post by RobF on 2005-02-18
My hardware: Dell 2300 desktop with integrated Intel i845 graphics chipset and with Dell E772c monitor

How can I force the Ubuntu Hoary Live CD (v. 5.04 alpha) to boot into a video mode with 1024x768 resolution and vert. synch 85 Hz?  If I boot the CD with default settings, my video hardware isn't properly recognized, and I wind up with a screen resolution of 800x600, the only other option available being 640x480.  There don't seem to be any boot options for setting the screen resolution.  Entering "linux screen=1024x768 vsynch=85" or "linux xres=1024x768" at the boot: prompt has no effect.

The earlier Ubuntu Warty Live CD v. 4.10 on my system boots into a screen with a resolution of only 640x480, and no other options are available under Computer > Screen Resolution.  This is despite the fact that I set the screen resolution at boot up to 1024x768 with the F4 key, and/or entered boot parameters similar to the above at the boot prompt.

Over the past 18 months, I've tried half a dozen different versions of live CD's of Morphix and Gnoppix and never managed to get them to work at the proper resolution and screen size on my system.  More than a dozen non-Morphix/Gnoppix live CD's work fine on my equipment, i.e. at 1024x768 and vsynch of 85 Hz.

On the other hand, the Beatrix v. 2005.1 live CD works properly on my system, with the boot option "linux26 vsynch=85".  Beatrix is a Ubuntu derivative, and as far as I know, it uses the Ubuntu boot software.  Needless to say, I'm mystified.

Can anyone tell me how I can set the proper video mode with the Hoary live CD?  Everything else (i.e. network, audio, disks, USB thumbdrives, etc.) seems to get set up fine on my system with that CD.

Thanks for your help.

Robert

---

### Post by RobF on 2005-03-11
Problem solved!

The most recent Hoary Live CD for Intel 386 (from 3-10-05, called hoary-preview-live-i386, or v.5.04 build 20041227ubuntu20) now recognizes my video hardware properly and by default gives me the resolution and vsynch I want when I'm running the CD live (1024x768, 85 Hz).  That makes all the difference!  Ubuntu looks like a nice distro.

One thing is odd though: non-Ubuntu hard disk partitions are nowhere to be found, neither in the system manager nor in the filesystem under /mnt.  I.e. I can't access my WinXP and other Linux partitions, not even for reading.  What am I missing?

Robert

---

