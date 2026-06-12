---
title: "power management"
date: 2010-04-30
forum: General Help
---

### Post by RichLouth on 2010-04-30
What happened to the "Do nothing" option for "When the suspend button is pressed" in Lynx?

It would also be useful to have a "Do nothing" option for "When the power button is pressed".

Personally, I find those keyboard keys really annoying.

---

### Post by happyhamster on 2010-05-01
In a terminal, type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set suspend to "nothing" (without the quotes). That option should now also be available in the main menu. Good luck.

---

### Post by RichLouth on 2010-05-01
Cheers happyhamster,

Should've thought about gconf-editor myself :)

I've already gone back to 9.04 though because the sound wasn't working. It was easier to go back to 9.04 than try and fix the sound.

---

