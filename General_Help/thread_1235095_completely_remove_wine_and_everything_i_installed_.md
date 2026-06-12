---
title: "completely remove wine and everything i installed with it"
date: 2009-08-08
forum: General Help
---

### Post by bodyharvester on 2009-08-08
on the UNR you get this sort of look in the attached image and you can see wine there, yet for some reason after removing i still have that section but instead of a wine glass i get a folder icon and some unreal stuff is still there

is there a command or something to remove it all properly?

i mean completely remove it no loose ends this time

also if any sudo commands are posted could someone post to verify it? safety first

---

### Post by Sidewinder1 on 2009-08-08
I've never had much success installing programs in wine, but, perhaps if you uninstalled, through wine, all of the programs, then in Synaptic totally remove wine. That may accomplish what you're trying to do. HTH, Side

---

### Post by bodyharvester on 2009-08-08
didnt work, although using synaptic to totally remove it freed up 65-ish Mb of space its still there with its icons, mocking me

any advice?

EDIT: thanks for the advice though :)

---

### Post by Sidewinder1 on 2009-08-08
You may get a more favorable response in the Wine subforum....As this question is specific to wine...
HTH,
Side

---

### Post by bodyharvester on 2009-08-08
> **Sidewinder1 said:**
> You may get a more favorable response in the Wine subforum....As this question is specific to wine...
HTH,
Side
  thanks, can a mod move it or something? or should i just restart it?

god i panicked when i coudnt access the forums for a moment there!

---

### Post by michy99 on 2009-08-08
The wine menu entries are at```
~/.local/share/applications/wine
```Delete that folder and everything should be gone.

---

### Post by bodyharvester on 2009-08-08
> **michy99 said:**
> The wine menu entries are at```
~/.local/share/applications/wine
```Delete that folder and everything should be gone.


thank you! deleting the folders finally removed it from the desktop-gui thing i have :)

---

