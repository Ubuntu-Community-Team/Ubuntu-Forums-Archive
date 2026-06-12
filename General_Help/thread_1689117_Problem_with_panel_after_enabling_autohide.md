---
title: "Problem with panel after enabling autohide"
date: 2011-02-16
forum: General Help
---

### Post by a_b_b_ on 2011-02-16
I was dabbling around with panel settings and i set the top and bottom panels to autohide and unchecked expand.
Now the bottom panel pops up properly when you bring the cursor over the area. However the top panel never pops up. I even made a new panel and when i select its orientation to 'top' ubuntu freezes up.
I even booted in the recovery mode with minimal graphics option. However the OS crashed as soon as it booted.
How do i revert to the old settings? Please help!

---

### Post by DanneStrat on 2011-02-16
> **a_b_b_ said:**
> I was dabbling around with panel settings and i set the top and bottom panels to autohide and unchecked expand.
Now the bottom panel pops up properly when you bring the cursor over the area. However the top panel never pops up. I even made a new panel and when i select its orientation to 'top' ubuntu freezes up.
I even booted in the recovery mode with minimal graphics option. However the OS crashed as soon as it booted.
How do i revert to the old settings? Please help!

I don't know why ubuntu locks up

when you're editing panels.

If I were you I would first restore the panels to default

settings.

To accomplish this, in a terminal run:

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

You may have to log out or reboot to have

the new settings applied and functioning properly.

Now try to do what you intended to do with the panels

in the first place and see if it's working.

Good luck.

---

### Post by a_b_b_ on 2011-02-17
SOLVED! :p
Though it was kind of indirect! I couldn't open up terminal directly so i pressed ctrl+alt+f2 and ran that code there. I later logged into recovery mode( normal mode still gave me problems) and ran it in minimal graphical config. Seemed fine! I then booted into normal mode and everything works fine!
THANKS!

---

### Post by DanneStrat on 2011-02-17
> **a_b_b_ said:**
> SOLVED! :p
Though it was kind of indirect! I couldn't open up terminal directly so i pressed ctrl+alt+f2 and ran that code there. I later logged into recovery mode( normal mode still gave me problems) and ran it in minimal graphical config. Seemed fine! I then booted into normal mode and everything works fine!
THANKS!

You're welcome.

---

