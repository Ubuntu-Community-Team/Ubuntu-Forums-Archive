---
title: "Grub takes 1 minute + to load"
date: 2010-01-04
forum: General Help
---

### Post by alket on 2010-01-04
Grub is displaying one black screen with underline cursor at top and statys about 1minute , how to fix it.

---

### Post by kybush on 2010-01-04
try this 

[http://undacuvabrutha.wordpress.com/2009/11/09/still-not-happy-with-the-speed-of-your-boot-in-9-10/](http://undacuvabrutha.wordpress.com/2009/11/09/still-not-happy-with-the-speed-of-your-boot-in-9-10/)

---

### Post by drs305 on 2010-01-04
One oft-reported cause of the delay is if the Grub 2 files are on one drive but the computer boots and looks at another drive first. For some reason, Grub 2 will spend time searching the first drive and will only move on to where the G2 files are located on the second drive after it finishes with the first.

The solution, if this is the case on your system, is to go into BIOS and change the boot order to have the computer boot the drive with the G2 files first.

---

