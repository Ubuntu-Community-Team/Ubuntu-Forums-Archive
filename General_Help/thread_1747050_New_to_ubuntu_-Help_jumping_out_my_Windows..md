---
title: "New to ubuntu -Help jumping out my Windows."
date: 2011-05-02
forum: General Help
---

### Post by terroristone on 2011-05-02
Hi guys, yes another noob here, i have previously had a "play" with ubuntu a few years back i liked how it was but really didnt have time to sit down for hours and configure everything, i have a few questions about ubuntu, i'd like to know with the current version how hard is it to get hardware working, i mean is it still a nightmare trying to find drivers and then loosing hair just to get my head around how to install them?
 
How is the current version with overclocked hardware? is there any software around to monitor and stress test with?
 
Will i have issues with my monitor configuration? as i use a single 30" in landscape and 2 20" in portrat mode.
 
Another thing that has me wondering is that with current games these days and their need to use all the hardware we have, running an emulator just to play games will be like throwing an ankor out of your car and trying to drive????
 
Any help on these subjects will be take seriously, 
 
Regards Andrew.

---

### Post by Mark Phelps on 2011-05-02
I've been doing the dual-boot Windows-and-Linux thing since the 7.04 days -- and personally, I've not found the transition any easier with the more recent Ubuntu versions.

If, anything, it has been harder ...

Version 10.10. for example, had known problems with restricted drivers and the ATI 6xxx series cards.  I've also read that there have been problems in th 11.04 betas with ATI drivers as well. Since I don't have a 6xxx series card, I don't know what happened in the end, but you can check the Video forum with your card model and see ...

As always, the easiest way to really see how well the current version detects your hardware and installs the proper drivers is to run from the LiveCD.

As to three monitors, the same video forum might have some info on that.  I'm not aware of it being available natively.

As to gaming, the situation hasn't really changed over the years, at least, for the better.  You still need Wine, or one of its add-ons, and you're still subject to individual performance on a game-by-game, version-by-version basis.

Best to check the WineHQ site (link below) to see the ratings for the games you want to run:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

As to hardware monitoring, I have used gkrellm a lot and found it to suit my needs.  Problem has been that the one in the Canonical distros has NOT been compiled with the right libraries included, severely limiting its usefulness.  Thus, to get all the hardare reqporting, you have to download and compile the source yourself.

There's also Conky, but that is a lot of hand-editing, but then, you can pretty much monitor anything for which you have an onboard sensor.

Good Luck

---

