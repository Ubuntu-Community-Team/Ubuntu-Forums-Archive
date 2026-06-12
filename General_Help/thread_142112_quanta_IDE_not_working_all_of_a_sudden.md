---
title: "quanta IDE not working all of a sudden"
date: 2006-03-09
forum: General Help
---

### Post by madubuntuer on 2006-03-09
It was working then stopped working all of a sudden. I ran it via sh to see if there any errors but they were none. THe strange thing is it seems to load properly into memory (in the processes list) however the only part of the GUI I ever see is the splash screen. I never see the usual windows and icons etc.

why is this happening?

I am using breezy with stock kernel and running it within gnome.

---

### Post by dbott67 on 2006-03-09
I've never used Quanta, but I had an app that was acting similarly.  I had to delete the .opera folder from my home directory.

Try looking for a .quanta (or something like it) folder in your home directory and moving/renaming it and then starting the app again.
```
mv .quanta .quanta.bak
```

Just a shot in the dark... :)

-Dave

---

