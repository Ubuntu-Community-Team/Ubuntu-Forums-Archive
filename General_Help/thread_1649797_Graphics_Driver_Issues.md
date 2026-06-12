---
title: "Graphics Driver Issues"
date: 2010-12-20
forum: General Help
---

### Post by ThomasTheTan on 2010-12-20
Hi-

I (unfortunately) am using an ati card (the HD 5770).  I got tired of dealing with updates messing with the proprietary drivers, and I read on [this]("https://help.ubuntu.com/community/RadeonDriver") page that the open source drivers now support 3D acceleration on my card.  Therefore, I decided to switch back to the open source drivers.  However, it seems as if I can't get them working.[URL="https://help.ubuntu.com/community/RadeonDriver"]
[/URL] 
I followed all of the steps found [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") to reinstall the drivers.  However, when I restarted my computer, the error that comes up when the proprietary drivers fail came up again (I think it was something like "X server wasn't able to start", but I can't remember for sure).  So I told it to go back to defaults and then restarted the computer.  I'm pretty sure that things aren't working correctly: I don't need to run ubuntu in low graphics mode, but compiz is certainly not working and the screen is "twitchy." 

There is a section on the original page ([here]("https://help.ubuntu.com/community/RadeonDriver#Testing%20The%20Driver")) that discusses how to test the drivers.  I don't get anything near the correct output when I run the first test, and my OpenGL string _does_ say "software rasterizer" (which it is not supposed to do).  I currently do not have an xorg.conf file. 

Any suggestions?

---

### Post by ThomasTheTan on 2010-12-20
Sticking with proprietary drivers for now...

---

