---
title: "gvim and DejaVu Sans Mono font - boxes!"
date: 2011-08-19
forum: General Help
---

### Post by Davorian on 2011-08-19
Hi all,

I'm looking for a little guidance on an issue I'm having with GVim on a standard Ubuntu Natty install.  After some recent changes (including the installation of Wine and the Microsoft base fonts) italic DejaVu Sans Mono characters have started appearing as boxes in GVim.

Attached is a screenshot of what this looks like.  This is very frustrating because I happen to like working with this font!  Other monospace fonts such as Liberation Mono and Andale Mono don't seem to be affected.

Any guidance on what might be causing this or how to solve it would be appreciated.

Cheers,
Davorian

---

### Post by Davorian on 2011-08-24
Fixed by running:

```
sudo dpkg-reconfigure fontconfig
```

I'm glad that this issue was fixed, although I'd appreciate if anyone could shed any light on what might have originally caused the issue (and why this specifically would have fixed it).

---

