---
title: "Ubuntu freezes after loading."
date: 2009-08-05
forum: General Help
---

### Post by madman118 on 2009-08-05
Pardon me, I am a total noob when it comes to Linux, so I came here. So my problem is that i have Ubuntu and Widows XP dual booted to my computer on a 80GB hard drive Ubuntu using 17GB of the drive. After I installed it it ran flawlessly even after several reboots mostly to test if this sort of thing was going to happen. This morning when booted Ubuntu it presented the loading screen, loaded and then the crap hit the fan. My monitor switched on and of several times and then froze on a blank screen, my monitor then informed me that there was no signal to the monitor. I booted windows and it ran as usual (like a 3 legged horse).

---

### Post by ajgreeny on 2009-08-05
Did you update to the new kernel 2.6.28-14 in the recent updates?  If so you may need either to reinstall a graphics driver, if you did so on the previous kernel, or you may need simply to boot to the older 2.6.28-13 (or whichever you had before the update) kernel, which will normally be the third item in grub menu.  The graphic card driver would be my guess.

---

### Post by madman118 on 2009-08-08
Problem solved, It was the graphics driver and monitor settings.

---

