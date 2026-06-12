---
title: "Kernel panic when starting X with latest kernel"
date: 2006-05-02
forum: General Help
---

### Post by Randomskk on 2006-05-02
As soon as I try to boot the latest kernel, the default boot option, it loads fine up until X. At this point, the screen flashes some static (this is normal for me) and then when it would normally be loading, it instead goes black and I'm left with some text, and at the bottom:
Kernel panic - not syncing. Aiee, killing interrupt handler
or something like that.

If I load recovery mode the system works, but typing "startx" there causes it to crash. If I boot an old kernel, the one marked Previous in my grub list, it works - although I need to swap to using the ATI driver instead of the fglrx I usually use.

However, I can not replicate the kernel panic under the old kernel.


Where would I start looking to solve this? I can't see anything interesting in the Xorg.0.log file, although it's a pretty big file.

Thanks for any help

(by the way, for some reason loading X in the old kernel brings up GNOME, so I'm stuck in GNOME for now.. with only one screen, as dual screen needs the fglrx drivers x_x)

---

