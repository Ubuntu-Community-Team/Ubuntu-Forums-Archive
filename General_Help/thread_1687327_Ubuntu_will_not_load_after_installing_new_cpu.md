---
title: "Ubuntu will not load after installing new cpu"
date: 2011-02-13
forum: General Help
---

### Post by axioanic on 2011-02-13
Hello, I have recently changed cpus in my dell e520 from a Celeron 346 to a core duo q6600. after switching the two I can no longer access my 32-bit Ubuntu 10.1 partition, the splash screen loads and then after that a garbled mess of pixels appears that somewhat look like my windows 7 desktop.

I am posting to see if anyone can help me fix this problem, I have already tried reinstalling Ubuntu by usb as well as cd, but to no avail. I have also tried installing mint-Linux 10, but only to have the same problem.

thanks in advance for the help

---

### Post by dabl on 2011-02-13
The Dell specs only show Celerons, Pentiums, and Core Duo CPUs up to E6300.  You wrote "Q"6600 -- did you get a Quad Core CPU? I would think it should support the _E_6600 ....

And, which video card did you get?

---

### Post by axioanic on 2011-02-13
Yes it is the quad core q6600, it is supported by the dell 2.4 bios.  As for the graphics card, it is a geforce gt 240 which I also installed recently although I am pretty sure that I had ran Ubuntu between installing the graphics card and cpu, although I could be wrong.


thanks for the help

---

### Post by dabl on 2011-02-13
I'm more concerned about the motherboard design and chipset than the BIOS, regarding support of the Quad Core CPU.  I'm not familiar with Dells, and I only skimmed the specs on their web site, but you need to verify that your motherboard model will in fact support a Quad Core CPU, if you haven't already. The fact that their specs only list CPUs up to Core Duo makes me wonder.  If it is a supported CPU, then maybe there's a video issue of some sort -- what you're describing sounds like a bit of video memory being dumped to screen -- I've seen that before.  Can you boot a Ubuntu Live CD?

---

### Post by axioanic on 2011-02-13
No, I have the same issue with live boots. I am beginning to think that it is a problem with the graphics card. After looking a little harder I found this thread: 

[http://ubuntuforums.org/showthread.php?t=1600807](http://ubuntuforums.org/showthread.php?t=1600807)

I am going to try what the last poster suggests and then I will report back the results

---

### Post by axioanic on 2011-02-13
that fixed it. thanks again for the help.

---

