---
title: "window boxes dont move smooth"
date: 2010-02-21
forum: General Help
---

### Post by kzpl17 on 2010-02-21
ok so i tried linux before but gave up now im trying it again and hopefuly ill stay with it, but my question is why do the window boxes when moved they dont move smoothly like in windows xp or 7. seems like its more rough when i move the windows around on my desktop, any one know why is that? im pretty sure i installed my graphic card. as i went to synthetic package manger and installed what i needed. 

and thanks

---

### Post by johngreth on 2010-02-26
You could try going to System->Preferences->Appearance->Visual Effects and trying out different settings. If it is a driver problem, I can't help, but anyone that can will need more info about your specific graphics card and driver

---

### Post by SecretCode on 2010-02-26
I've seen this in Ubuntu **and** in a fresh install of XP - if the video drivers aren't right, you get jumpy effects on things like dragging windows around.

Check System > Admin > Hardware drivers - and if no luck, post your video card details here.

---

### Post by BZF on 2010-02-26
[COLOR="Blue"]I'd do a few things:
Update Drivers
or change the visual effects settings

your graphics card either isn't very high, or the settings/drivers aren't working right[/COLOR]

---

### Post by Mark Phelps on 2010-02-27
If you installed a recent Ubuntu version (9.04 or 9.10) and you have one of the discontinued legacy ATI cards/chips, you won't be able to use ATI drivers because their support was dropped last may.

So. before you try forcing a driver update and totally hosing your display ... report back with the video driver card/chip present in your machine.

If you don't know how to do that, open a terminal and enter "lspci".

---

