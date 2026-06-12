---
title: "Move multiple windows at once?"
date: 2009-08-07
forum: General Help
---

### Post by ltwinner on 2009-08-07
Is it possible to move multiple windows at once in ubuntu? I can click and drag a box around icons on the desktop and then move several of them at once. Can something similar be done for moving windows?

---

### Post by P4man on 2009-08-07
you can with compiz. You must have compositing enabled, and install CCSM:

```
sudo apt-get install compizconfig-settings-manager
```

Then in compiz settings, enable the "group and tab" plugin (name could be wrong, translating from dutch).

Check the keybindings, but I think by default you select windows by pressing Super+S, then group them with super+G. now they are "glued together", if you move one, the other will follow.. Ungroup with super+U.

More useful perhaps is tabbing them. Select two windows, then press super+t.  One window will now be the "other side" of the other window. you can flip them over either by hovering your mouse in the middle of the title bar, or by pressing super+left or super+right.

Reconfigure as you see fit :)

---

