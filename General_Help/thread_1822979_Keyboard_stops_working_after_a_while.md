---
title: "Keyboard stops working after a while"
date: 2011-08-11
forum: General Help
---

### Post by grayfafhrd on 2011-08-11
Hello,

This is the first time I've got a major problem with Ubuntu (I started with version 5), and this one is particularly frustrating.
I'm running Ubuntu 11.04 on my old (2007) desktop PC. Occasionally, but more and more often now, the keyboard just stops working. The mouse is still fine. When I shut down, I would sometime notice that the "stop crash report generation" process fails. Then the shutdown sequence stops at some point, and I am forced to do a hard shutdown, power down for a while, and reboot. If I don't wait after power off, the keyboard freeze would occur again at any time during the start up sequence. I even had a keyboard freeze after manually switching to the Windows boot.

Any suggestions?

---

### Post by dino99 on 2011-08-11
time to watch logs and maybe do a fresh new install if this one is too old and have been upgraded many times.

---

### Post by Bart92 on 2011-08-11
> **grayfafhrd said:**
> Hello,

This is the first time I've got a major problem with Ubuntu (I started with version 5), and this one is particularly frustrating.
I'm running Ubuntu 11.04 on my old (2007) desktop PC. Occasionally, but more and more often now, the keyboard just stops working. The mouse is still fine. When I shut down, I would sometime notice that the "stop crash report generation" process fails. Then the shutdown sequence stops at some point, and I am forced to do a hard shutdown, power down for a while, and reboot. If I don't wait after power off, the keyboard freeze would occur again at any time during the start up sequence. I even had a keyboard freeze after manually switching to the Windows boot.

Any suggestions?

Automatic crash report generation is part of what Apport does. In  previous years, the Ubuntu developers have turned off Apport shortly  before the release of that version of Ubuntu, and turned it on in the  new development version 
Seems like everyone has this *
You could try to establish a ssh connection from the other pc and see if it is still alive or switch to a other usb port in your computer.

---

