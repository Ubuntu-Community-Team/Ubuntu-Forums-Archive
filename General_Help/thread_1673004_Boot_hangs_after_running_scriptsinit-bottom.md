---
title: "Boot hangs after running /scripts/init-bottom"
date: 2011-01-21
forum: General Help
---

### Post by Minn3h on 2011-01-21
Data points:
-Ubuntu 2.6.32-19-server
-First symptom, blinking cursor on boot
-After removing quiet from the boot options I see that it runs through the init scripts and then hangs
-I can boot to command line by putting "rw init=/bin/bash" but don't know what to do once I get there to diagnose the problem
-The system is primarily a fileserver/XBMC htpc
-The system was running for several months before this restart so I can't identify a specific change as the problem unless it's because...
-Recently I made changes to all of the disks by switching from JBOD to software raid (with mdadm)

Any suggestions for identifying the problem or finding more symptoms?

---

### Post by Minn3h on 2011-01-21
Further evidence emerges. The more I fiddle the more convinced I am that it's a problem with the video. It really seems like the system is working normally except that whenever it tries to switch to any sort of graphical mode the signal is lost. (Which is odd since this is a server install and all I want is a commandline). I've tried every GRUB boot option I can find to no avail: nomodeset, vga=ask, vga=771, noapic, acpi=off 

So the question is what does ubuntu server use for the graphical text output and how can I adjust it? Seems like it would be a simple framebuffer and I have no idea how that would not be compatible but...

---

### Post by Minn3h on 2011-01-22
I should have checked it sooner but my system is outputting video to my PCI video card (Geforce 8400GS) all the way up to the point I've described and then Ubuntu is outputting the graphical command line to my motherboard's onboard video card. So now I just have to figure out how to have it use the PCI card instead.

---

### Post by Minn3h on 2011-01-22
I'm going to mark this as solved, I guess I'll just deal with the fact that the console is being outputted to my onboard video card. There's no way to disable it in the BIOS of the Intel BOXD510MO.

---

### Post by Minn3h on 2011-01-22
I guess I was wrong. After reinstalling the nvidia drivers I'm back to a black screen on any output...

---

### Post by Simonpro on 2012-03-26
Did you find a solution to this? I have the same problem...

---

