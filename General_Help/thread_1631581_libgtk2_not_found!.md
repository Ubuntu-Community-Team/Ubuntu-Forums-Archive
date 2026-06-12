---
title: "libgtk2 not found!"
date: 2010-11-26
forum: General Help
---

### Post by mikmalot on 2010-11-26
I'm trying to configure pcsx, but I keep getting an error saying 
checking for GTK2... no
configure: error: *** libgtk2 not found!

I then go and try to install libgtk2, but I'm told that i already have a later version than the one I was trying to install. So I check my software center, and sure enough I have it installed. Suggestions?

---

### Post by mikmalot on 2010-11-28
Nothing? Am I just missing something incredibly obvious?

---

### Post by Decatf on 2010-11-28
It is looking for the development files which are in a separate package. You probably want to install libgtk2.0-dev

---

### Post by mikmalot on 2010-11-28
It turns out I had that one installed, but I did a bit of digging, and I ended up installing libgtk2.0-cil-dev, and it worked. Thanks for the push in the right direction!

---

