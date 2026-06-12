---
title: "Frequency is out of range"
date: 2005-03-13
forum: General Help
---

### Post by lauriesherrod on 2005-03-13
With a lot of help, we installed UBUNTU on my son's computer using a borrowed monitor.  When we got home and put his monitor on it, it will not boot - it says 'FREQUENCY IS OUT OF RANGE, 80K/75HZ'.  The monitor settings say 720x400 70 HZ 1024x768.  I was told to try XF86FORCEPROBE=yes sudo dpkg-reconfigure xerver-xfree86.  I tried that and it asked me about all kinds of hardware, but nothing about the monitor.  Any more ideas - or hints about which questions dealt with the monitor (maybe I missed it?).

---

### Post by rosslaird on 2005-03-13
Does it give this error when the computer is off but the monitor is on? Try turning both off, then turn the computer on first -- then the monitor. It should not give you an error unless the video card and the monitor are not playing nice together.  It is possible to get sync errors laters, in the starting of an X session, but in that case it's a different matter. You should at least be able to boot up. If not, it may a hardware (compatibility) problem. And at the risk of sounding overly obvious: make sure you have the monitor plugged into the the correct port.

Edit:

OK, in re-reading your post it looks like you can boot up after all and that this is an X problem. If so, you can specify your monitor's settings in the xorg config file (or XF86Config-4 file, depending on which X server you have). Mine is xorg.conf (in /etc/X11), and the relevant section says this:

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	56-75
	VertRefresh	30-81
EndSection


dpkg-reconfigure doesn't always ask you everything you need.

---

