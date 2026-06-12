---
title: "Virtual Terminal &lt;control&gt;&lt;alt&gt;&lt;f2&gt;"
date: 2009-09-03
forum: General Help
---

### Post by M!SF!TS on 2009-09-03
i want to set my virtual terminal key binding from <ctrl><alt><f2> to <super> hot key, how do i do this ? i tried keyboard shortcuts System>Preferences>Keyboard Shortcuts but i need to know the terminal command to virtual terminal...

i honestly dont care how i set my shortcut... compiz setting manager, keyboardbindings, a hotkey program... i just want to set it and have it work...

any help?

thanks.

---

### Post by M!SF!TS on 2009-09-04
Really no one can help with this ? ...WOW!

im going to take a back seat on this thread...  :popcorn:

---

### Post by DaithiF on 2009-09-04
well chvt is the command to switch virtual terminals.  for me (9.04) i need to sudo for it to work when switching INTO a virtual console:
```
sudo chvt 1
```
switching back to my graphical screen i don't need sudo:
```
chvt 7
```

---

