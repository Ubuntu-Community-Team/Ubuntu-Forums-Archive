---
title: "How do I make conky &quot;stick&quot; to the background?"
date: 2012-02-09
forum: General Help
---

### Post by ConchX on 2012-02-09
Hello UbuntuForums.

I'm having a little problem with conky. I'm quite new to editing conky settings. but it works good so far.

However, whenever I click the button on the lubuntu to show the desktop, it minimizes all my windows and conky too, so I have to click to show all windows again to allow conky to show up again. Is there a way to stick it to the desktop, so showdesktop/iconify all windows doesn't affect it?

Thank you. :popcorn:

---

### Post by drmrgd on 2012-02-09
I think you just need to set "own_window" in your .conkyrc file to normal or override (I can't never remember which and usually just guess and check!).  My window attributes section - just for an example:

```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints below,undecorated,sticky,skip_taskbar,skip_pager

```

Hope it helps

---

### Post by Rodney9 on 2012-02-09
A good source of Conky tips, even though it's from Arch, is - 

[https://wiki.archlinux.org/index.php/Conky](https://wiki.archlinux.org/index.php/Conky)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by ConchX on 2012-02-09
Thank you for the quick reply drmrgd :)

I have own_window set to "normal"
It was orginially set to "Override" but when set with that option, conky wouldn't even display at all :confused:

---

### Post by drmrgd on 2012-02-09
Thanks for the Arch Wiki link Rodney.  Seems to have a nice collection of many of the hacks and workarounds I've found in various places!

Conch, did setting own_window to "normal" fix it, or is that the way it was set up before?  If not, I might recommend posting your .conkyrc to the [Conky Mega Thread ]("http://ubuntuforums.org/showthread.php?t=281865"), where the conky pros will definitely be able to help more more than conky amateur like me :D

---

