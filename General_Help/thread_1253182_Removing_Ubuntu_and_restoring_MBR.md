---
title: "Removing Ubuntu and restoring MBR?"
date: 2009-08-29
forum: General Help
---

### Post by the lemming on 2009-08-29
I have Ubuntu and XP on a laptop however I wish to remove Ubuntu and just have the laptop boot into XP.

Anybody know how I restore the Master Boot record to allow me to do this?

Cheers

---

### Post by mikewhatever on 2009-08-30
Try SuperGrub live cd.

---

### Post by oboedad55 on 2009-08-30
> **the lemming said:**
> I have Ubuntu and XP on a laptop however I wish to remove Ubuntu and just have the laptop boot into XP.

Anybody know how I restore the Master Boot record to allow me to do this?

Cheers

Just boot from your Windows CD and get to the repair console. At the command prompt type "fixmbr", press "enter". You'll be asked if you're sure, and so on. That will do it.

---

### Post by Bucky Ball on 2009-08-30
You might also want to try 'fixboot' when at the windows repair.

---

### Post by the lemming on 2009-08-30
[QUOTE=oboedad55;7868981]Just boot from your Windows CD and get to the repair console. 

The Laptop in question only has a Recovery CD and not the full instillation CD.

Would the recovery CD still help?

---

### Post by Bucky Ball on 2009-08-30
Yep, you should be able to recover (install) and repair you OS with it. It will have a full installable copy of Windows on there. It's basically a Windows cd on the recovery partition and the disk you created should allow you to do anything you would with a regular install cd.

---

