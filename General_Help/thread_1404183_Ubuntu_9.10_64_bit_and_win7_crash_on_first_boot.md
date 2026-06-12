---
title: "Ubuntu 9.10 64 bit and win7 crash on first boot"
date: 2010-02-11
forum: General Help
---

### Post by mattcmgb on 2010-02-11
Hi all,
I have an alienware m17x laptop with 2 hardrives, on primary is win7 and on secondary is ubuntu 9.10.
 
The problem I have is if I boot (using Grub) into linux it crashes before the ubuntu logo pops up and locks up completely, needing a hard reset. If I boot linux again, all is fine. I can't copy the text that comes up when it crashes, is this logged anywhere so that I can post it?
 
The same thing kind of happens in win7, on first boot (via Grub) I get the windows logo for about a second then BSOD and it reboots (so fast I can't see the error). If i boot again into win7 it boots fine.
 
Any help with this would be much appreciated. The win7 issue is not a problem really as I hardly use it, however this started happening after the ubuntu install and so i figure they are related.
 
Many thanks
 
Matt

---

### Post by Mark Phelps on 2010-02-11
Yeah, I read you said that the Win7 crash is not an issue -- but if the BSOD is pointing to a hardware problem, that COULD be an issue that you're not seeing.

Suggest when you next get into Win7 you go into Computer --> Properties --> System Protection --> Advanced --> Startup and Recovery and uncheck Automatically Restart.

Then, the next time you get a BSOD, it won't restart and you will have enough time to write down the info and research the STOP code to see if it's a hardware-related error.

---

### Post by mattcmgb on 2010-02-11
Mark,
Ok thanks I will try that and capture the error. Is there anyway of doing the same for Ubuntu, i.e. does it log startup errors anywhere?
 
Many thanks
 
Matt

---

### Post by mattcmgb on 2010-02-11
OK I have isolated the BSOD:

driver_irql_not_less_or_equal 0x000000D1

This seems to only occur when my usb wireless mouse is plugged in, damn annoying as it is really usefull.

Any ideas.

Cheers

Matt

---

