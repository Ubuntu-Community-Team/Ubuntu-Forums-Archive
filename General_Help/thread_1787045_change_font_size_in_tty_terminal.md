---
title: "change font size in tty terminal"
date: 2011-06-20
forum: General Help
---

### Post by gizmo720 on 2011-06-20
I am running Ubuntu 10.04. When I first installed it, the virtual terminals had a good font size. After a few weeks, I set the visual appearance setting to normal (in the gui desktop). Doing this required me to install third party graphics drivers from nvidia. in installed fine, and my gui desktop still functions as I would expect, however, all of the virtual terminals now have a much larger font size, as does the ubuntu boot logo.

---

### Post by gizmo720 on 2011-06-22
I figured it out. In the grub configuration, I had to add ```
        set gfxpayload=1024x768x32

``` to the boot commands. For anyone wanting to do this, you can figure out what resulution your computer supports by running "vbeinfo" in the grub command line.

---

