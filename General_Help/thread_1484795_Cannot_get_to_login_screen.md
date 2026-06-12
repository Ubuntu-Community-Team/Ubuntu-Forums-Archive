---
title: "Cannot get to login screen"
date: 2010-05-16
forum: General Help
---

### Post by rnfel on 2010-05-16
Hi Guys

My installation of Ubuntu 8.04 has been working fine for over a year now, but as of Friday, I cannot login.  The login screen is never displayed, instead I get something that looks a bit like a messed up version of my laptop's startup screen, showing Toshiba and Intel logos.  (See the attached image)

I doubt that the problem is my screen, because I can still log into Windows on the same machine, and it looks fine.  I've tried the fix X option on the Ubuntu recovery screen, fcsk, and I've tried running dpkg-reconfigure xserver-xorg from the root command prompt.  None of these approaches rectified the problem.
 
I have a Radeon HD2600 graphic card, in case anyone would like to know.

Does anyone have an idea how to fix this so that I can log in again?  Help will be much appreciated, thanks!

Riaan

---

### Post by rnfel on 2010-05-16
Bump...

---

### Post by rnfel on 2010-05-16
Bump, again.

---

### Post by rnfel on 2010-05-17
For future reference, running aticonfig --initial fixed the problem.

---

