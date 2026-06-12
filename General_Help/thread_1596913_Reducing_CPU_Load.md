---
title: "Reducing CPU Load"
date: 2010-10-14
forum: General Help
---

### Post by Aspiring_Failure on 2010-10-14
Hi, I just wanted to know if I could do anything to reduce the CPU load on Ubuntu.

Right now I'm averaging about 10% when I'm not even doing anything, which doesn't seem right. (XP, on the other hand, idles at just 0 - 1%)

---

### Post by Dex73 on 2010-10-14
STEP 1: Go to System/Administration/System Monitor to look for rouge applications sucking memory and other applications that are in use in the background that you don't need. (If your not sure what they do, their usually best left alone)

STEP 2: Go to System/Preferences/Startup Applications  to keep them from starting up.

---

### Post by Aspiring_Failure on 2010-10-14
Actually, that's already been done. All I have left on right now are the power, sound, and network managers + the keyring stuff.

Before I turned off the start-ups, I was idling at almost 40%, maybe higher.

---

### Post by Prohibited on 2010-10-14
How powerful is the CPU that you are running? Also, try going to System -> Preferences -> Appearance -> Visual Effects and disabling Compiz ("No visual effects")

---

### Post by Aspiring_Failure on 2010-10-14
I'll try that, but would compiz really hog that much *idle* CPU?

And as for my CPU, it's an AMD Sempron 3000+ 1.8 GHZ. 
On the same note, I've noticed myh cpu seems to cycle between "Modes", the first one being when It's not active, it reads at 990 MHZ. When It's active, though, It'll read as 1.8 GHZ. 

Could this mean when it says 10%, It's out of the 990 MHZ mode, and therefore really only about 5%?

Edit: Turning off Compiz did reduce me down to a cool 2 - 4%, but I'd still like to know if there's anything else I could do to reduce CPU load. (So that, maybe, I can get down to about 5% with Compiz on)

Also, would installing a videocard reduce Compiz's CPU load?

---

### Post by Aspiring_Failure on 2010-10-15
Under the resources Tab, the system monitor is always shown as using the highest % of CPU. Is the % shown out of my CPU's total capacity, or out of the current load?

I'm beginning to think the system monitor may be skewering the actual results, because it Itself is using a lot CPU.

---

