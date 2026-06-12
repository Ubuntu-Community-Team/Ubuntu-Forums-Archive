---
title: "jpilot freeze my palm since karmic"
date: 2009-11-10
forum: General Help
---

### Post by plh on 2009-11-10
Hello,

Until jaunty, I used to sync my palm Z22 to my desktop-pc using jpilot, which worked quite right and was fast enough.

Since I upgraded to karmic, launching a sync from my palm just freezes it (strange small, almost pixel-sized, patterns appear on the palm screen and stay there until the palm is completely discharged: no response to screen - or buttons - actions).

Did anyone experience the same problem and if so, did this person find the workaround?

Thanks in advance!

---

### Post by plh on 2009-11-21
Up ;-)

Did someone experience the same problem?

Thanks in advance!


> **plh said:**
> Hello,

Until jaunty, I used to sync my palm Z22 to my desktop-pc using jpilot, which worked quite right and was fast enough.

Since I upgraded to karmic, launching a sync from my palm just freezes it (strange small, almost pixel-sized, patterns appear on the palm screen and stay there until the palm is completely discharged: no response to screen - or buttons - actions).

Did anyone experience the same problem and if so, did this person find the workaround?

Thanks in advance!

---

### Post by Eynowd on 2010-01-02
I'm certainly seeing it. My Z22 goes nuts as soon as I plug it into my Karmic box. It still works OK on my Eeebuntu netbook.

---

### Post by plh on 2010-01-06
Yeaaah!
I was beginning to think I'm alone in the dark ;-)
It does not seem to mean much to many people however...

Any idea, folks?
Thanks in advance!

---

### Post by jelabarre on 2010-01-12
No, there seems to be little concern for making our nice, simple, *NON-PHONE* devices work anymore.  It seems the majority of the lemmings out there have made the foolish headlong rush into smartphone-land.
 
Sorry, folks, but if I can no longer sync my palm device to my computer, and cannot get a cheap, non-phone replacement for it, my next move will be back to *PAPER* for my "PDA" (ironic as that name would be).  At which point the hopeless struggle will instead become getting some Linux address/calendar app to print to DayRunner "Size 3" format.

---

### Post by woody setzer on 2010-02-14
I'm also unable to sync.  Using a z22, Worked in Jaunty, but not in karmic.  As soon as I plug in the Z22, the battery changes to the charging icon, then in about a second, the Z22 freezes and the screen develops a sort of color houndstooth pattern.  What have you all tried to make it work?
Woody Setzer

---

### Post by woody setzer on 2010-02-14
For me there was an easy fix, which I learned from another thread on this forum (from a post by [I]Freelance Physicist; November 3rd, 2009 at 12:54 PM.. 					 					 				

[/I]Double check to make sure /etc/modules has a visor entry (usually this gets erased by upgrades, but not this time).
goto System -> Preferences -> PalmOS Devices
Under Devices tab, make sure your device has settings:
Type: USB
Timeout: 2
Device: /dev/ttyUSB1
Speed: 115200

Add the Pilot Applet to a panel (right click on panel, "Add to panel...", select Pilot Applet).

> **woody setzer said:**
> I'm also unable to sync.  Using a z22, Worked in Jaunty, but not in karmic.  As soon as I plug in the Z22, the battery changes to the charging icon, then in about a second, the Z22 freezes and the screen develops a sort of color houndstooth pattern.  What have you all tried to make it work?
Woody Setzer

---

### Post by dleslie on 2010-03-14
This happens to me too; seems like the Z22 is no longer supported by the Visor module as of Karmic?

---

### Post by dleslie on 2010-03-14
> **woody setzer said:**
> Double check to make sure /etc/modules has a visor entry (usually this gets erased by upgrades, but not this time).
goto System -> Preferences -> PalmOS Devices
Under Devices tab, make sure your device has settings:
Type: USB
Timeout: 2
Device: /dev/ttyUSB1
Speed: 115200

This worked for me, Thanks!

---

