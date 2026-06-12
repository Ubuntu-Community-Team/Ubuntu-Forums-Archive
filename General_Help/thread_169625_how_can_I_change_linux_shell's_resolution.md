---
title: "how can I change linux shell's resolution?"
date: 2006-05-03
forum: General Help
---

### Post by mankyuhan on 2006-05-03
When I say linux shell, I mean the shell when you hit crtl+alt+F1.
(You can come back just by hitting alt+F7, at least for me)

I tried Dapper Live CD, and there was an option to select different screen resolution like 1024x768x16bit.. 

by selecting that, I could have smaller Ubuntu boot splash which I like.:D 

But, I failed to install nvidia graphic driver for dapper, so I returned to Breezy.  THen,..I can't figure out how to set the resolution of the shell.

Does anyone know about this?
I searched but, found nothing](*,) .  Please HELP!!!

---

### Post by htinn on 2006-05-03
The way you set the console shell resolution is by changing the kernel line in the grub "menu.lst" file:

```
kernel		/boot/vmlinuz-2.6.15-21-k7 root=/dev/hdd1 ro quiet splash vga=791
```

vga=788 (800x600x24)
vga=791 (1024x768x24)
vga=794 (1280x1024x24)

---

### Post by yoink23 on 2006-05-03
I don't want to hijack this thread, but I think I might have a related question.  It's always bothered me that when I get to the bottom of the screen in console mode, the prompt goes of the bottom of the screen, as if my monitor isn't calibrated correctly.  But it is, as the screen inside gnome is perfectly centered without anything going off the screen.

Any solution out there?

---

### Post by mankyuhan on 2006-05-03
Wow .. Thanks htinn!!!  I'll try it now!

---

### Post by Seaman on 2006-05-03
[QUOTE=htinn]The way you set the console shell resolution is by changing the kernel line in the grub "menu.lst" file:

```
kernel		/boot/vmlinuz-2.6.15-21-k7 root=/dev/hdd1 ro quiet splash vga=791
```

vga=788 (800x600x24)
vga=791 (1024x768x24)
vga=794 (1280x1024x24)[/QUOTE]
Nice! But what about if I want it higher? Like 1600x1200x24?

---

### Post by mcduck on 2006-05-03
[QUOTE=yoink23]I don't want to hijack this thread, but I think I might have a related question.  It's always bothered me that when I get to the bottom of the screen in console mode, the prompt goes of the bottom of the screen, as if my monitor isn't calibrated correctly.  But it is, as the screen inside gnome is perfectly centered without anything going off the screen.

Any solution out there?[/QUOTE]
Most monitors use calibration per refresh rate/resolution, and as they are different in CLI mode, you need to calibrate it again for this new resolution/refresh rate.. (Usually monitors are able to remember settings for couple of diferent resolutions/refresh rates, so this shouldn't mess your screen in Gnome :)

---

### Post by htinn on 2006-05-03
Okay, I did some digging around and found this:

[http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash](http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash)

So, basically:

vga=799 (1600x1200x24)

---

### Post by Seaman on 2006-05-03
[QUOTE=htinn]Okay, I did some digging around and found this:

[http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash](http://gentoo-wiki.com/HOWTO_Framebuffer:Bootsplash:Grubsplash)

So, basically:

vga=799 (1600x1200x24)[/QUOTE]
Thanks! :D

---

### Post by yoink23 on 2006-05-03
Thanks, mcduck!

---

