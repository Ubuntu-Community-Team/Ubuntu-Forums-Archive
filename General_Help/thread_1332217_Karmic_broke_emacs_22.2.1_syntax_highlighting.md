---
title: "Karmic broke emacs 22.2.1 syntax highlighting"
date: 2009-11-20
forum: General Help
---

### Post by flostre on 2009-11-20
Hi,

on my office PC, the upgrade to Karmic Koala broke syntax highlighting in emacs 22.2.1. Also, the C++ menu is still there but empty. On my laptop I have no such problems. Since I have .emacs file, I tried starting without it and also with the .emacs from my laptop, but the problem remains. Syntax highlighting works in no file I tried - C++, bash, Makefile, awk. But it still works in emacs' own buffers :(

As a remedy I tried emacs 23.1.1, but there's still no syntax highlighting. The C++ menu works though.

BTW, this again showed me that I don't really like Emacs. However, it is my default editor because I *really* like the keystrokes. I also use regexp search/replace and rectangle editing quite often. If somebody could suggest a good replacement that also offers these features, I'd be happy to try it out.

Edit: I tried xjove, but even when called without any arguments, it immediately exits with

```

A command window has exited because its child exited.
Its child's process id was 18855 and it exited with return code 1.

```

I'm also trying mped, but I can't yet say that it lives up to what it promises.

Edit2: Sometimes RTFM helps. Emacs calls syntax highlighting "fontifying" or "font lock mode". To activate it, press M-x and type "global-font-lock-mode". I still don't know why the update to Karmic disabled it though.

---

