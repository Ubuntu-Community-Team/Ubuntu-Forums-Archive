---
title: "automatic indentation in vim"
date: 2010-12-17
forum: General Help
---

### Post by c2tarun on 2010-12-17
in using emacs, if we want to auto indent a c program we just select the whole program by C-x h and then press tab, it indents.
is there any way to do this in vim??

---

### Post by Brandon Williams on 2010-12-17
In command mode: ggVG=

And if that doesn't make complete sense (how could it not :-): "gg" moves the cursor to the beginning of the file, "V" starts visual line mode, "G" moves the cursor to the end of the file (thus selecting the whole file), and "=" performs the re-indentation.

---

### Post by c2tarun on 2010-12-17
> **Brandon Williams said:**
> In command mode: ggVG=

And if that doesn't make complete sense (how could it not :-): "gg" moves the cursor to the beginning of the file, "V" starts visual line mode, "G" moves the cursor to the end of the file (thus selecting the whole file), and "=" performs the re-indentation.

Thanks :)

---

