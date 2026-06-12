---
title: "No Spanish Dvorak keyboard layout in console mode"
date: 2011-08-07
forum: General Help
---

### Post by marcosaedro on 2011-08-07
Hi all, 

I recently switched to Dvorak layout, and found a nice  Spanish variant, which respects the labels of most non-letter keys that  are present in my Spanish physical keyboard. The swap was easy in the  graphical environment (Gnome/Unity). However, in text mode (tty1 through  6) this layout doesn't seem to be available. 

After installing  console-data, a directory keymaps appears in /usr/share, but it doesn't  contain Spanish Dvorak. However, it does contain Spanish and Dvorak-US,  which means that I could theoretically merge them into a Spanish Dvorak  keymap. Xorg apparently gets the keymap from  /usr/share/X11/xkb/symbols/es,  which is in a different format but could also serve as inspiration. 

Is there other place where I should search for the keymap? (locate "*.kmap*" doesn't yield anything useful)

Is there documentation about editing keymaps?

Is there an easier way of getting Spanish Dvorak in the virtual terminals?

---

