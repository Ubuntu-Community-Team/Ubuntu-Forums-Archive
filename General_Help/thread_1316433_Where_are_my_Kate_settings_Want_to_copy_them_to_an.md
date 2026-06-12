---
title: "Where are my Kate settings? Want to copy them to another computer"
date: 2009-11-05
forum: General Help
---

### Post by a cup of tea on 2009-11-05
I like the way I have Kate (the text editor) set up on this computer. I want my settings, mostly my color scheme, on another computer. How can I do this?

---

### Post by VolkerLanz on 2009-11-06
> **a cup of tea said:**
> I like the way I have Kate (the text editor) set up on this computer. I want my settings, mostly my color scheme, on another computer. How can I do this?

KDE applications store their settings in $HOME/.kde/share/config/. In Kate's case it's a little more complicated than usual because Kate is a so called KPart (it can integrate into other applications), so there are a number of config files in that directory for it, but all of them are beginning with "kate". Copy these to the same location on your new machine.

---

### Post by a cup of tea on 2009-11-08
Thanks. :D

---

