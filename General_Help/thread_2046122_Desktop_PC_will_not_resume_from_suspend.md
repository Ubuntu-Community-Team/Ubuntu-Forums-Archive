---
title: "Desktop PC will not resume from suspend"
date: 2012-08-22
forum: General Help
---

### Post by ziggutas on 2012-08-22
New PC dual booting with Windows XP and ubuntu 12.04 LTS will not resume from suspend. Windows has no problem with standby.

 Ubuntu will go into suspend ok, screen goes into low power mode , PC suspends, fans off, power light blinking. When attempting to resume the PC wakes up, fans on , power light steady, but nine times out of ten the screen will stay in low power mode and keyboard will be dead. The mouse LED underneath will light up but after about 20 seconds go out. The only option is to turn the power off and reboot.

Sometimes the computer will wake from suspend, display the screen login and I can start a session but very soon the mouse pointer and screen display will freeze and keyboard become unresponsive.

I was hoping kernel updates might solve the problem but nothing so far.

I'm a fairly new ubuntu user.  Processor is Intel® Core™ i3-2120 CPU @ 3.30GHz × 4; Graphics Intel® Sandybridge Desktop x86/MMX/SSE2 .

---

### Post by nothingspecial on 2012-08-24
Prefix changed from lubuntu to ubuntu.

and bumped

---

### Post by ziggutas on 2012-08-24
Thank you, so kind. I was wondering about the prefix and just about to bump!

---

### Post by ziggutas on 2012-08-25
Bump

---

### Post by ziggutas on 2012-08-26
Um.

---

### Post by ziggutas on 2012-08-31
Anybody?

---

### Post by ziggutas on 2012-09-05
One last bump before I give up. You never know.

---

### Post by ziggutas on 2012-11-04
Well, after a couple of months looking for a solution, going up and down various dead ends and coming unstuck in the process, it looks as though my problem is finally solved.

Updated the ASrock UEFI to a later version, and after about a day spent trying to get all the settings right (was unable to boot into windows at one point, then trying to fix that was unable to boot into ubuntu as well. Repaired the damage with a live cd session and boot-repair; phew.) I can now suspend and resume from suspend without problem. Hooray!

---

