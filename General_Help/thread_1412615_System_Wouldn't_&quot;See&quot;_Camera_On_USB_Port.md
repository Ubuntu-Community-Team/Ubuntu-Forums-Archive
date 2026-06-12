---
title: "System Wouldn't &quot;See&quot; Camera On USB Port"
date: 2010-02-21
forum: General Help
---

### Post by JSeymour on 2010-02-21
System specifics:

Ubuntu 9.10 (Karmic Koala) Desktop - current on all security & recommended updates
Dell PowerEdge 1600SC Server, dual 3.2GHz, 4GB RAM, PERC 4 RAID
2-port PCI USB card (can't recall manufacturer)

Everything's been working fine, USB-wise.  I've got the keyboard and mouse plugged into the integrated USB ports.  I use the two USB 1.1 ports on the additional card for whatever else I want to plug in.  I've successfully used a couple of thumb-drives, my camera and my Centro (via JPilot and pilot-xfer) on both ports in the past.  Last use was the Centro with pilot-xfer.  Mostly I've been using what I'll call "USB port 1."

Plugged the camera into USB port 1 this morning: Nothing.  Nothing in the logs or dmesg.  Hmmm... Okay, I don't feel like messing with this, so I'll just reboot and see if that restores things.  Nope: Still wouldn't talk.  Plugged a thumb-drive into the same port.  No go.  Plugged the same thumb-drive into USB port 2 and it worked.  Moved the thumb-drive back to USB port 1 and now it saw it :confused:  Plugged the camera into that same port and now it worked :confused:

Somehow I *suspect* it all has something to do with pilot-xfer use on USB port 1.  For reasons that aren't clear to me, use of a Palm device on USB ports is kind of twitchy: You have to plug the Palm device in, press the "sync" button and, within a window of a few seconds, then start pilot-xfer.

Can anybody give me a clue as to what might've happened here and how to fix this problem?

Thanks,
Jim

---

### Post by JSeymour on 2010-02-22
No clues?

---

### Post by no2498 on 2010-02-22
sounds like you had a bad unmount 
plug the pilot-xfer back in then unmount it before you turn it off right click the icon unmount now turn it off
hope this helps

---

### Post by JSeymour on 2010-02-23
> **no2498 said:**
> sounds like you had a bad unmount With Palm devices, TTBOMK, nothing is ever mounted.

> **no2498 said:**
> plug the pilot-xfer back in then unmount it before you turn it off right click the icon unmount now turn it offPilot-xfer is a  Linux/Unix application that you use to "talk to" a Palm device.  There is no icon or anything else upon which to click to unmount anything.

JPilot, which *is* a point-n-drool application, has no "unmount" button, either.  It does have a "Quit" selection.

> **no2498 said:**
> hope this helps
Thanks for the follow-up.

Jim

---

