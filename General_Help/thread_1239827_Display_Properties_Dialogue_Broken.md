---
title: "Display Properties Dialogue Broken"
date: 2009-08-13
forum: General Help
---

### Post by DrHow on 2009-08-13
When I go System -> Preferences -> Display, the app does not start correctly.  To the extent that it starts at all, it starts very slowly, and it appears to put a drag on performance.  (Indeed, it slows the echoing of my typing here.) There may appear in the upper left hand corner of the screen a little green box with the notation "Unknown".  Mostly the app does not start at all.  Its window opens, but it remains blank - except once, when it also was announcing "unknown".  The monitor is a fairly new LG 22" LCD with native 1920x1080 resolution.  The properties dialogue has worked before and correctly showed the monitor by name, along with correct available resolutions.

The above is the short explanation.  There is a bit more to it.  I was using this monitor on two computers using an Iogear KVM switch.  Both have Ubuntu 9.04 installed.  All was well.  I was starting a hard drive upgrade on one of them.  Call it "A".  I used a live CD for gparted, and it did not choose a valid monitor resolution by default.  Rather than use the VGA boot mode, I plugged in a more nearly normal monitor (17" CRT) on the KVM switch.  That did not work either.  Confused, I tried booting the other machine, "B", with the gparted live CD back on the 1080p monitor.  That did not work (by default) either.  So I booted the Ubuntu installed on B, and it had gone to a lower resolution (which was ugly).  (I am supposing that B, which was running when I had the 17" monitor plugged in, had seen something via the switch that got it confused about the display.)  When I checked Display Properties on B, the 1920x1080 option was no longer even present.  It dawned on me that the communication with the monitor through the KVM switch might be causing the problem.  So I bypassed the switch and rebooted B.  It could now properly identify the monitor and had its correct resolutions, so I was back in business on B.  Then I plugged the monitor directly into A (no switch) and rebooted A again.  As it turns out, A is still running at 1920x1080.  However, the Display Properties Dialogue no longer works properly on A, as described in the first paragraph.  I rebooted and the problem did not go away.  This is not serious now; but I was planning on hooking up a second monitor (which my graphics adaptor will support), and I need for that Display Properties app to work then.

What could cause this?  What might fix it?

---

### Post by P4man on 2009-08-14
what videocard do you have? If its an nvidia card, did you install the binary driver for it? If so, just use the nvidia applet to change resolutions. If you installed the binary ATI driver, use (or install) the catalyst control center. If you didnt install any drivers, perhaps try installing "resolution switcher" in add/remove programs;

---

