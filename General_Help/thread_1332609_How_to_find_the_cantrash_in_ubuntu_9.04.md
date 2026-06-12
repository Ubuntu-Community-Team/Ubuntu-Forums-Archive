---
title: "How to find the cantrash in ubuntu 9.04"
date: 2009-11-20
forum: General Help
---

### Post by roquin on 2009-11-20
How to find the cantrash in ubuntu 9.04? do not tell me press alt+f2 or application system toll ? becaouse i try that

---

### Post by emigrant on 2009-11-20
you mean the Trash?

```
~/.local/share/Trash/files
```

---

### Post by Minsky on 2009-11-20
If you mean how to display the trashcan on the desktop, then open a terminal window and type:

```
gconf-editor
```

Goto **apps>nautilus>desktop**, and in the large right hand pane place a tick/check mark in the box next to **trash_icon_visible**.

---

### Post by Slimbo on 2009-11-20
lmfao, you made my day. It's a *trash can ( in other words, Trash )*, not *cantrash* :lol:

---

