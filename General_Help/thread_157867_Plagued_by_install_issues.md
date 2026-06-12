---
title: "Plagued by install issues"
date: 2006-04-10
forum: General Help
---

### Post by Azio on 2006-04-10
This is my first time with Linux, so bear with me if I sound stupid.

Basically I installed Ubuntu to my USB hard drive per the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=80811"). I'm not sure if my problems are related to my using a USB drive so I decided to bring them here.

First off, near the end of the install process, it suddenly crapped out. Went to a grey screen with rapidly-scrolling black text, too fast to read.
[IMG]http://www3.telus.net/northlight/azio/images/linux/scroll.jpg[/IMG]

After a minute or two it finally stopped, and the aftermath can be seen below.
[IMG]http://www3.telus.net/northlight/azio/images/linux/panic.jpg[/IMG]

So I rebooted the machine, started Linux. It appears to boot okay, but it complains about something called Locale twice during the startup process:
[IMG]http://www3.telus.net/northlight/azio/images/linux/locale.jpg[/IMG]

Finally, X Server fails to start because it can't find any screens. This is the output:
[IMG]http://www3.telus.net/northlight/azio/images/linux/xserver.jpg[/IMG]

I have a hand-built machine with an AMD Athlon 64 3200+, 1GB (2x512) RAM, ATI All-In-Wonder X800XL, and a Creative Sound Blaster Audigy 2. The motherboard is DFI LanParty UT NF4 Ultra-D. The hard drive is a 40GB Hitachi Travelstar in an nGear USB Mobile enclosure. I'm running the latest AMD64 release.

---

### Post by towsonu2003 on 2006-04-14
not that I have any clues or anything but, did you check the .iso's md5sum you downloaded before burning to CD? also, using a slow burning speed might help. it basically looks like a bad install, you might wanna re-try. 

Before going for a reinstall though: at the end, when it says "no monitor found", looks like xserver (X, graphical interface - windows and stuff) was not configured... you could try "sudo dpkg-reconfigure xserver-xorg" or alternatively, you could try "sudo dpkg-reconfigure -a". The first will reconfigure X, the second will reconfigure everything (will take a long time).

---

