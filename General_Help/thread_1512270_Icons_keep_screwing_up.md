---
title: "Icons keep screwing up"
date: 2010-06-17
forum: General Help
---

### Post by kaldor on 2010-06-17
Ever since Lucid, didn't happen on openSUSE or previous Ubuntus. Why is this jumble/icon cutoff happening?

---

### Post by wojox on 2010-06-17
You could try resetting them.

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by hansdown on 2010-06-17
Hi kaldor.

Same thing here.

I right clicked the panel, and added a shut down button for now.

---

### Post by cap10Ibraim on 2010-06-17
Same thing here  , I noticed everything was ok until I installed applications that use the panel by themselves like googleDesktop , Opera ,..

---

### Post by kaldor on 2010-06-18
I didn't even alter the top panel too much. It's just annoying that I have to change the theme or type a command to fix such a minor issue that occurs so much.

---

