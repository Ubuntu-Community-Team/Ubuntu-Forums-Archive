---
title: "Ubuntu and Ham Radio! DSTAR help needed..."
date: 2010-12-31
forum: General Help
---

### Post by bradRNstyle on 2010-12-31
I am assuming there are some other amateur radio operators out there using Ubuntu.  Is there any Linux based radio programming software for the Icom IC2200 and/or the Icom IC-91AD?  I have the windows(xp) software for them and the cables, I was just thinking it would be nice to do it in Linux.... since the DSTAR network is built in Linux.

Suggestions?


Thanks! =)

---

### Post by rlhorn on 2010-12-31
Sorry, I really can not help you on this, and apologize for Hijacking your post, but was just wondering if it is just me.

All these companies that use Linux for their servers, networks, etc... you would think **SHOULD** have software fo Linux!  But no, just Windows and sometimes Mac. (Amazon comes to mind with the Kindle.  Wheres Kindle for Linux!)

Whats going on?

Just a concerned user.

Again, I apologize,
Robert

---

### Post by bradRNstyle on 2011-01-02
You would think so, their entire network is built on Linux VOIP servers.  Maybe it will work in WINE...

---

### Post by coldraven on 2011-01-02
I just typed "icom" in the Synaptic Package manager and got this. See screenshot.
Any use?

---

### Post by todak on 2011-01-02
> **bradRNstyle said:**
> Maybe it will work in WINE...
It does work very well in Wine. But to transfer data using the serial interface you need to translate the unix serial ttyS0, ttyS1, etc. port names to something the windows program understands. For example, I use the following: 
```
ln -s /dev/ttyS0 ~/.wine/dosdevices/com1
```
I use the serial port for programming my Yaesu VX-2, Icom IC-2100, IC-2200, IC-W32A and my Radio Shack PRO-2067 trunking scanner, using the Windows-based software for each rig. I have not tried it with the rig control software for my IC-746, but that is due to my laziness in building the CI-V interface, even though I have the controller IC and breadboard. :p Hope this helps!

---

### Post by bradRNstyle on 2011-01-13
Thanks everyone.  =)

---

