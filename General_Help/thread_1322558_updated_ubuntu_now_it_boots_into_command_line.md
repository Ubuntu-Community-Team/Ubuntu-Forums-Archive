---
title: "updated ubuntu now it boots into command line"
date: 2009-11-11
forum: General Help
---

### Post by AmishFury on 2009-11-11
some time ago i installed 8.04 on family member's laptop as a backup plan in case they break windows... i did a wubi install at the time

well they broke windows so until i can find out how to fix that problem i booted them into ubuntu and tonight i ran the update manager (hasn't been updated in some time as you may have guessed) rebooted now it goes to some "busybox" thing and i have no idea what to do... 

this is quite urgent as they will want their computer usable in the morning and i'm having serious trouble finding the answer

---

### Post by MichealH on 2009-11-11
At the box can you CTRL-ALT-F7? That key combination gets you into X sever mode

---

### Post by AmishFury on 2009-11-11
that does nothing

---

### Post by MichealH on 2009-11-11
I think it is a wise idea to reset gnome and to do that you will loose your settings so try:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by AmishFury on 2009-11-11
well it seems to have fixed itself

now if only windows would be so kind as to do the same thing

i'm tempted to go with backing up files and reformatting

---

