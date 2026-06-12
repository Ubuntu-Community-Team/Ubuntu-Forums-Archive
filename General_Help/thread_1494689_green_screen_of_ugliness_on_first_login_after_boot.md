---
title: "green screen of ugliness on first login after boot"
date: 2010-05-27
forum: General Help
---

### Post by roberto.tomas on 2010-05-27
I kinda recall this happening when I installed hotkeys. But I've removed hotkeys from my applications on-startup and I still get this weird effect -- it only occurs on the very first login after a bootup.

It sets the screen to some green or purple color for a second -- it writes to the screen very slowly, filling it up from top to bottom with this ugly random color. once it is full (about a second), it's gone, and the boot up continues as normal.

This *used* to come right before when the hotkeys splash screen appeared. But now that I've removed hotkeys from my start up apps (and system alltogether), I still get the screen on boot.

"hotkeys hit my computer with the ugly stick!" please help :)

---

### Post by roberto.tomas on 2010-06-06
bump and update:
the color screen only loads when I log in to gnmoe -- it only loads AFTER the first time I log in after a boot up, and it doesn't always load :)

---

### Post by dino99 on 2010-06-06
try:
 sudo dpkg-reconfigure plymouth
 sudo dpkg --configure -a

---

### Post by roberto.tomas on 2010-06-06
> **dino99 said:**
> try:
 sudo dpkg-reconfigure plymouth
 sudo dpkg --configure -a

thanks for the suggestion, although it didn't work. (just tried it)  -- might be my own fault because I said that the problem was only showing up imediately after a boot .. but I meant the opposite. it never shows up on boot, only on after closing a session and starting a new one.

---

### Post by roberto.tomas on 2010-06-27
bump

---

### Post by dino99 on 2010-06-27
few questions:

do you only use genuine ubuntu repo ? (if not, deactivate them, clean the cache, then update, upgrade)

is your video driver activated ? (system admin hardware driver)

what says logs ?

---

### Post by roberto.tomas on 2010-06-27
thanks :)

> **dino99 said:**
> do you only use genuine ubuntu repo ? (if not, deactivate them, clean the cache, then update, upgrade)

I've had this problem for quite a while now .. I since have installed xubuntu desktop (but dont really use it just yet) and it has changed my login screen -- but I used to have this problem even before that change.

> is your video driver activated ? (system admin hardware driver)

no. I'm on a PowerPC and there is no hardware driver available for me :S

> what says logs ?
any log in particular I should be looking at?

thanks dino

---

