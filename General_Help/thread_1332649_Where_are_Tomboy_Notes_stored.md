---
title: "Where are Tomboy Notes stored?"
date: 2009-11-20
forum: General Help
---

### Post by OldGrantonian on 2009-11-20
I would be grateful if anyone could tell me where the data files for Tomboy Notes are stored.

I do:

cd ~
ls -la

There are plenty of directories beginning with ".", but no ".tomboy"
.

---

### Post by P4man on 2009-11-20
Its been moved:
[http://ubuntuforums.org/showthread.php?t=1275844](http://ubuntuforums.org/showthread.php?t=1275844)

---

### Post by emigrant on 2009-11-20
i have a .tomboy

---

### Post by sharm on 2009-11-20
Please read here: [http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

Before 1.0, notes and everything else were in ~/.tomboy.  After 1.0, notes moved to ~/.local/share/tomboy and other stuff moved appropriately (this is following FreeDesktop.org standards).

---

### Post by OldGrantonian on 2009-11-21
> **P4man said:**
> Its been moved:
[http://ubuntuforums.org/showthread.php?t=1275844](http://ubuntuforums.org/showthread.php?t=1275844)

That worked! Thanks :)

---

### Post by ianp5a on 2012-01-04
Great thanks. 
I found my old notes in a backed up "**local/share/tomboy**"
I copied the individual note files to a new installation and they correctly appeared when I started Tomboy again.

---

