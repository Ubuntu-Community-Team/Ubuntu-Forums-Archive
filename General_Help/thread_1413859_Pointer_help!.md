---
title: "Pointer help!"
date: 2010-02-22
forum: General Help
---

### Post by chill32 on 2010-02-22
Uhm, probably some of you guys are getting annoyed with newb questions but i have kind of an annoying issue. see, that i downloaded KDE to test it out but then I removed it because I felt it was just horrible. Thing is though now I'm using gnome and I love it but i cant get rid of the pointer that kde had. so now no matter what theme I pick the pointer stays the same. i tried changing the pointer but it just stays the same. I'm getting really annoyed at it.

---

### Post by quixote on 2010-02-24
I've never tried to change cursors or pointers, but I remembered seeing something once which might be relevant, and when I checked my own system, maybe this would work.  There's something called gconf-editor for fine-grained control of gnome.  Start it by using a terminal and typing ```
sudo gconf-editor
```(I'm actually not sure you need the "sudo".)  I'm also not sure it's installed by default.  If you don't have it, you can install it via synaptic.

Once you're in gconf-editor, go to desktop > gnome > peripherals > mouse.  One of the entries is "cursor_theme".  If you select it and right-click, you can choose to edit it.  Mine, with a standard cursor, says "Human" (without quotes).

---

