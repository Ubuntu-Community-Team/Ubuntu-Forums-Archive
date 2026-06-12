---
title: "Menus &amp; Toolbars tab missing?"
date: 2010-05-13
forum: General Help
---

### Post by Xavier Oddmon on 2010-05-13
I did a fresh install about two days ago to Lucid Lynx 64 bit. It's very nice, but there are a few things that are bugging me. This is one of them:
I used to be able to go to system -> preferences -> appearance, and there was a tab called "Menus & Toolbars". It had, amongst other things, the ability to enable **editable menu accelerators**. This tab is gone in Lucid Lynx. Is there some way I can get that functionality back? I can't find a gconf key to do the same, but I could be missing it.

---

### Post by blazemore on 2010-05-13
> **Xavier Oddmon said:**
> I did a fresh install about two days ago to Lucid Lynx 64 bit. It's very nice, but there are a few things that are bugging me. This is one of them:
I used to be able to go to system -> preferences -> appearance, and there was a tab called "Menus & Toolbars". It had, amongst other things, the ability to enable **editable menu accelerators**. This tab is gone in Lucid Lynx. Is there some way I can get that functionality back? I can't find a gconf key to do the same, but I could be missing it.

The Gnome developers removed this because they felt it was not suitable for a front-end integrated configuration utility.
They felt these kinds of configuration tweaks were best left to third-party applications.
Luckily, Ubuntu-Tweak has just what you need. Install it by clicking [here]("apt:ubuntu-tweak"), then run it and click Gnome Settings. Should be most everything you need, plus more!

---

### Post by tecywiz121 on 2010-05-27
The gconf keys you are looking for are in

/desktop/gnome/interface/toolbar_*

---

### Post by jlukescott on 2010-12-06
Thank you guys so much! I had had this question for months but didn't know exactly what words to search for.

---

