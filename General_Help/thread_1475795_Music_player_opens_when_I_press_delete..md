---
title: "Music player opens when I press delete."
date: 2010-05-07
forum: General Help
---

### Post by Existance0 on 2010-05-07
Well, I can't use the delete key for anything if I press it, it opens up a music player. If the music player is already open the delete key does nothing.

---

### Post by Existance0 on 2010-05-07
Well, I said screw it and reset gnome...
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

This seemed to fix it. But if I press print screen this now opens said music player. >.>

---

### Post by Existance0 on 2010-05-07
Heres a picture of the music player notice it also adds an icon to the bar in the bottom right.

---

### Post by Dhee on 2010-05-07
System > Preferences > Keyboard shortcuts.

Check if there is an entry for Rythmbox somewhere. If there is, delete it.

I don't know how to put the key's to default though.

---

### Post by Existance0 on 2010-05-07
Hm, it appears something is wrong with my keyboard. If I press print screen the keyboard shortcuts program says that I pressed "XF86AudioMedia".

---

### Post by Existance0 on 2010-05-08
So basically... print screen is mapped to "XF86AudioMedia", left arrow key is mapped to "XF86AudioMedia" my right arrow key is mapped to "XF86AudioMedia" and delete is mapped to "XF86AudioMedia". Yes, it's reading all four of these keys as a single key.

---

