---
title: "Glade Help"
date: 2010-07-29
forum: General Help
---

### Post by ferret man on 2010-07-29
I'm trying to write a GUI for a program I coded using Glade Interface Designer but I can't figure out how to build it. All I end up with is a .glade file that I can't do anything with but open in the editor. how do I make it run? Thanks.

---

### Post by uRock on 2010-07-29
> **ferret man said:**
> I'm trying to write a GUI for a program I coded using Glade Interface Designer but I can't figure out how to build it. All I end up with is a .glade file that I can't do anything with but open in the editor. how do I make it run? Thanks.

Navigate the terminal to the directory containing the file, then run ```
ls -il <filename
``` The permissions need to be ```
-rwx------
``` for it to be executable. If it does not have that permission, then run ```
chmod 700 <filename>
```

---

### Post by ferret man on 2010-07-29
> **uRock said:**
> Navigate the terminal to the directory containing the file, then run ```
ls -il <filename
``` The permissions need to be ```
-rwx------
``` for it to be executable. If it does not have that permission, then run ```
chmod 700 <filename>
```
But it's just an XML file... that won't do anything. :/

---

