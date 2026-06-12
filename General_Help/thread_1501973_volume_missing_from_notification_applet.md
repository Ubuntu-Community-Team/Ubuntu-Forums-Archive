---
title: "volume missing from notification applet"
date: 2010-06-04
forum: General Help
---

### Post by phillychease on 2010-06-04
title says all.
the sound works and all.
plus theres an empty space which seems like there use to be an icon there.

if it helps, i have an ICEauthority error when i turn on my computer.

---

### Post by wojox on 2010-06-04
Did you remove Indicator Applet? You will need to add it back if so.

---

### Post by phillychease on 2010-06-04
i tired that and i also tried restarting the whole panel.
nothing works.

---

### Post by wojox on 2010-06-05
> **phillychease said:**
> i tired that and i also tried restarting the whole panel.
nothing works.

You restarted with these two commands:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by phillychease on 2010-06-05
never mind i got it.
i had problems with the ICEauthority.
i fixed that and the volume control came back.

---

