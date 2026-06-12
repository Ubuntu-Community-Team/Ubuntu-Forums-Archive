---
title: "X11 directory"
date: 2010-07-28
forum: General Help
---

### Post by whizzlife on 2010-07-28
Hi everybody,
            I found out that if you go inside /usr/bin/X11 directory, you can cd to X11 unlimited numbers of times. Is it the bug? or is it something that no one noticed or don't care?
Well i have ubuntu 9.04!!

---

### Post by Ozymandias_117 on 2010-07-28
The "X11" directory in there is a sym-link pointing to the current directory. I assume it's there for backwards compatibility. Since it's pointing into the current directory, yes, you can enter it infinite times :P.

---

### Post by chopinhauer on 2010-07-28
> **whizzlife said:**
> 
            I found out that if you go inside /usr/bin/X11 directory, you can cd to X11 unlimited numbers of times. Is it the bug? or is it something that no one noticed or don't care?


It's not a bug, it's a feature! Once upon a time X binaries where in /usr/bin/X11 or /usr/X11R6/bin, while the rest was mainly in /usr/bin. Since then this distinction was abandoned, but in order not to break old software and configuration that assume this distinction /usr/bin/X11 was symlinked (symbolically linked) to /usr/bin.

They are the same directory, so /usr/bin/X11 contains a subdirectory named X11.

The GNU/Hurd operating system goes one step further and symlinks /usr to /.

---

