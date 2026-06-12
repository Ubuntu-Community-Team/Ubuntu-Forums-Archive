---
title: "Firefox GUI font (inconsistent with desktop)"
date: 2010-05-08
forum: General Help
---

### Post by lucasreece on 2010-05-08
Wondering if anyone can help me here.

I've changed all fonts in appearance preferences to Liberation Sans with monochrome rendering but Firefox GUI font doesn't change (see screenshot).

Any ideas how to fix this please? I've not seen this in any other apps as yet, just Firefox so not sure if this is a Firefox issue or indeed Gnome or Ubuntu.

Many thanks.

Lucas Reece.

---

### Post by notceecee on 2010-05-08
@ Firefox

```
Edit > Preferences > Content
```

---

### Post by lucasreece on 2010-05-08
I can do that but I want to change the GUI font (menu bar, bookmarks and navigation toolbar fonts).

Please see the attached screenshots.

---

### Post by notceecee on 2010-05-08
Add this to your ~/.gtkrc-2.0

```
gtk-font-name="Liberation Sans 10"
```

---

### Post by lucasreece on 2010-05-08
> **notceecee said:**
> Add this to your ~/.gtkrc-2.0

```
gtk-font-name="Liberation Sans 10"
```

Tried this but it hasn't changed anything in Firefox.

The .gtkrc-2.0 file didn't exist so I created an empty file, saved it to the root of my home folder, added the code to the file, saved, launched Firefox and still no change. What am I doing wrong?

Running Lucid 10.04 and Firefox 3.6.3.

---

### Post by lucasreece on 2010-05-10
BUMP.

Any idease please folks?

---

### Post by Zorael on 2010-05-10
Any **~/.fonts.conf** file? I don't see how it would mess up Firefox without messing up GNOME as well, but can't hurt to try. Rename it and restart FF.

---

