---
title: "Winmodem problem"
date: 2006-06-10
forum: General Help
---

### Post by whitehornmatt on 2006-06-10
I have a lucent winmodem in my pc, to my surprise it was detected automatically in dapper, and /dev/ttyLTM0 was created. But when I went to dial it would never work, it dialed but I never got a carrier. It dials up fine in windows, and worked perfectly in breezy. Is there anything I need to do to get it working, or should I just go and get a hardware modem to save all the trouble. I would rather not get a new modem, but I am getting sick of having to do so much to get it working.

---

### Post by loell on 2006-06-11
if you already have a budget for an external modem, then go for that.. its worth it.

---

### Post by Apple 101 on 2006-06-11
A quick Google search for "Lucent winmodem+linux" should help you.  I got mine working, when the modem wasn't even detected some years back.

---

### Post by blastus on 2006-06-21
I had a similiar problem in Dapper also. The modem would dial but never connect. The trick is to uninstall the default driver completely before installing yours. Using the -v option with the modprobe command, as in ```
sudo modprobe -v ltserial
``` will tell you where the modules are being inserted from.

Have you tried my guide [HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial)](http://www.ubuntuforums.org/showthread.php?t=198730)?

---

