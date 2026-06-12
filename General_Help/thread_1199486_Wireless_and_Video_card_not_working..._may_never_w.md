---
title: "Wireless and Video card not working... may never work"
date: 2009-06-29
forum: General Help
---

### Post by RawCaret on 2009-06-29
Firstly, I'd like you all to know that I've been a fan of Linux for a long time and I still am.  It just never works for me, which is kind of saddening because I hear other people say it works so well for them.  Anyway...

 My wireless card doesn't work (it did)
My video card doesn't work properly (it almost did)
The system hangs for no reason I could find anywhere

 Hardware in question:
- Linksys WMP300N (Broadcom chipset)
- NVidia 8800 GTS 512
OS: Jaunty
*********************************
The wireless card worked immediately after I activated the Broadcom STA drivers.  Video looked good at 1080p (native resolution of my monitor).
Installed the drivers for the video card.  Scaling was off, so it cut off about an inch in every direction. Disabled flat panel scaling in settings which fixed the problem (for now).
Started torrent program to try seeding.  In 15 minutes or less the system would freeze every time torrents were running.  I eliminated every possible problem that could have caused a hang:  writing lots of data to an NFS volume, lots of network traffic with both Broadcom and Ndiswrap drivers, conflict with video card drivers, chipset power throttling incompatibility.
Through the course of troubleshooting this problem I changed, disabled and re-enabled drivers for my video card and my network card multiple times.  Each time I did something with the video card it would go back to improper scaling.  Now for some reason it is stuck like that.  Ever since I tried ndiswrapper drivers my network card has not worked.  I have tried uninstalling them and reinstalling the old drivers, restarting after every little step. 

The sound sounds like a crappy mp3, too... but I can live with that for now.  I digress...

 I don't expect anybody to be able to come up with an answer for these problems.  I feel like the only thing to do is buy different hardware unless somebody comes out with new drivers that actually work 100% (never going to happen).  Every time I've tried to install Linux on a computer something like this has happened.  I'm losing my faith!  I hope very few people have this kind of trouble.  I've been fighting with this OS for almost 2 weeks now.  Have a nice day.

---

### Post by t4thfavor on 2009-06-29
I have 2x 9600gt's running flawlessly in my PC, (Desktop) As for the broadcom, I haave given  up on them in favor of atheros, or senao cards for linux Intel's work good for laptops.

Which driver version for the nvidia are you running, I believe the 185 driver is what I am using, and I have extremely good luck with it.

Good luck on the broadcom though ( I would suggest downloading or prouring insome other way the latest broadcom firmware, and then putting it in the firmware directory)

---

### Post by RawCaret on 2009-06-30
> **t4thfavor said:**
> I have 2x 9600gt's running flawlessly in my PC, (Desktop) As for the broadcom, I haave given  up on them in favor of atheros, or senao cards for linux Intel's work good for laptops.

Which driver version for the nvidia are you running, I believe the 185 driver is what I am using, and I have extremely good luck with it.

Good luck on the broadcom though ( I would suggest downloading or prouring insome other way the latest broadcom firmware, and then putting it in the firmware directory)
I am running Nvidia version 180.  I tried installing 185 and no matter what I did it would start up in low graphics mode.  I seem to already be using the latest broadcom firmware.  I'm back to where I was.

---

