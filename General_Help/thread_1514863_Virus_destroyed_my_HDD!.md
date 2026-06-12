---
title: "Virus destroyed my HDD?!"
date: 2010-06-21
forum: General Help
---

### Post by Blue_Pepper on 2010-06-21
Hi there. I really hope someone might have an answer for me.  I recently bought a new Acer Travelmate 5740G preloaded with Windows7.  I loaded anti-virus (avast pro) on it. 

Two days after starting to use it, I got a message from avast (after leaving it on the internet over lunch time) that it can't start it's scanning engines...  I restarted and everything went downhill from there.  
After that first restart some other apps also started malfunctioning.  The next day (after a proper shut-down) when I powered the laptop up again, it couldn't find the HDD anymore!  I went into the BIOS and it didn't detect the HDD either, but on the bootable devices screen it showed the HDD.

So I decided to give the new Ubuntu Live CD a chance, thinking that (1) it would format my HDD and get rid of whatever it was that caused the crash and (2) also gain the added security of linux while I'm at it to prevent similar future events.  The first assumption soon prooved to be QUITE wrong.

I tried everything. Even some code like the following in an attempt to kill the bug (assuming it was a big to start off with):

```
sudo swapoff -a
sudo dd if=/dev/zero of=/dev/sda bs=32k
```[FONT=monospace]
[FONT=Verdana]and some other code with shred random and two passes.

nothing worked.

After running each process, I tried to re-install ubuntu.  All would go well until I have to restart. Then it's the same story again: [/FONT][/FONT]> No bootable device detected[FONT=monospace][FONT=Verdana] 
Any ideas?!  Did the virus bugger my HDD up completely, [/FONT][/FONT][FONT=monospace][FONT=Verdana]or is this virus maybe hiding in the BIOS[/FONT][/FONT][FONT=monospace][FONT=Verdana]?!
[/FONT][/FONT]

---

### Post by philinux on 2010-06-21
Guarantee comes to mind. Hard drive may have been a dud. Happens sometimes.

---

### Post by Blue_Pepper on 2010-06-21
> **philinux said:**
> Guarantee comes to mind. Hard drive may have been a dud. Happens sometimes.

Do you think they'll still put it through as a warranty claim after the "hell" I've the HDD through?

---

