---
title: "broken man pages"
date: 2010-06-12
forum: General Help
---

### Post by NYKevin on 2010-06-12
Most man pages, across all sections (particularly 1 and 6), are broken for me.  When I try to look at them, I see what appears to be raw binary instead of text (if I've done this correctly there should be an attached screenshot).  Weirdly enough, it doesn't apply to man(1), but it does apply to man(7).  I've tried switching to tty6, running catman and mandb -c, to no avail.  I'm stumped, does anyone have any advice?

I suspect that it is somehow reading compressed data or something since running
```
zcat /usr/share/man/man1/cat.1.gz | less
```gives reasonable output (it isn't nicely typeset like man pages are supposed to be, but it is readable), but cat(1) appears to be broken when I use man cat.

Special notes:
I'm running 64-bit and have some kubuntu- and xubuntu-related packages installed, as well as xscreensaver and related packages.  10.04 LTS (Lucid).

---

