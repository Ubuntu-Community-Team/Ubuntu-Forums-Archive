---
title: "Grub error 21"
date: 2009-09-27
forum: General Help
---

### Post by Kurt Arndorfer on 2009-09-27
Had a frustrating situation and thought I would share the solution with others who may be in the same boat. 

I have been running 8.10 and Windows 7 on separate drives for some time without problems. Yesterday I got "error 21" out of nowhere, and was not able to boot into either os. After much cursing and trying every grub-related fix I could find, I went into BIOS and saw that the Windows drive was set to boot first, then the Linux drive. I changed the boot order and everything now works perfectly.

I have no idea what caused the problem, or why my fix worked. All I know is that I have a working computer again. Hope it helps someone.

-Kurt

---

