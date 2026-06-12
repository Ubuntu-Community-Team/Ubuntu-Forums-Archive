---
title: "Brightness applet is laggy, setting through command line isn't permanent."
date: 2010-11-07
forum: General Help
---

### Post by pinapl on 2010-11-07
The brightness applet in Lucid used to have instant changes. Since I upgraded to Maverick, it became very laggy. It takes 10 seconds to shift from one brightness level to another, so I quit using it.
I found a way to switch it via the command line:
```
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
```
However, this does not last; The brightness set in the brightness indicator or the power management menu soon overrides the value set in the command line. I would really like to know how to
a) make the brightness applet less laggy, or
b) make the brightness applet leave my brightness alone.
Any help is appreciated, thanks.

---

### Post by pinapl on 2010-11-07
The brightness app is linked to the power management. Is there a way to recompile power management while leaving the brightness control out?

---

### Post by pinapl on 2010-11-12
bump

---

### Post by pinapl on 2010-11-25
Found the solution.
open the gconf-editor, look under apps/gnome-power-manager/backlight.
Uncheck "enable"
Now power management cannot affect the backlight brightness, which lets me keep control of it.

Out of curiosity, how many people actually saw this page?

---

