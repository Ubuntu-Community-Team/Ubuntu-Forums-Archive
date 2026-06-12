---
title: "Gnome Shell notifications not working"
date: 2012-01-21
forum: General Help
---

### Post by sgage on 2012-01-21
I'm talking about the notifications that slide up from the bottom. They were working fine until yesterday. I can't think of anything I might have done to turn them off. It works properly in another account on the same machine.

Any ideas?

---

### Post by dino99 on 2012-01-21
into a terminal:

gnome-shell --replace

---

### Post by sgage on 2012-01-21
> **dino99 said:**
> into a terminal:

gnome-shell --replace

Alas, that did not fix it. (Is 'gnome-shell --replace' the same as 'Alt-F2 r' ?)

---

### Post by sgage on 2012-01-21
Well, after some troubleshooting I figured out that whatever it was, it was something in the file ~/.config/dconf/user. I mv-ed it, and all was well. I just had to reconfigure a couple of things, like favorites on my launcher and my wallpaper. All back to normal!  :KS

---

