---
title: "How to get rid of usplash?"
date: 2006-06-20
forum: General Help
---

### Post by ralf57 on 2006-06-20
Hi all,
is there a way to get rid of booting usplash and restore the good-old list of boot messages?
Thanks in advance.

---

### Post by JSchwage on 2006-06-20
Try removing the package "usplash" in Synaptic. ;)

---

### Post by ralf57 on 2006-06-20
[QUOTE=JSchwage]Try removing the package "usplash" in Synaptic. ;)[/QUOTE]

Thank you,i'll try and let you know

---

### Post by Ramses de Norre on 2006-06-20
Remove "splash" from your kernel line in /boot/grub/menu.lst.
You'll need to remove it from the line starting with ```
# defoptions=
``` and run sudo update-grub to apply it to all kernels and automaticaly apply to all new and updated kernels in the future.

---

### Post by ralf57 on 2006-06-20
[QUOTE=Ramses de Norre]Remove "splash" from your kernel line in /boot/grub/menu.lst.
You'll need to remove it from the line starting with ```
# defoptions=
``` and run sudo update-grub to apply it to all kernels and automaticaly apply to all new and updated kernels in the future.[/QUOTE]

So i don't need to remove the package as suggested by JSchwage,dont'i?

---

### Post by Ramses de Norre on 2006-06-20
I don't know, I guess it's safer to disable it first =)

---

### Post by ralf57 on 2006-06-20
thank you again

---

### Post by ralf57 on 2006-06-20
One moment Ramses, i meant ubuntu boot splash
[http://www.simplifiedcomplexity.com/images/screenshots/dapper/flight3/gfxboot-theme-splash-small.png](http://www.simplifiedcomplexity.com/images/screenshots/dapper/flight3/gfxboot-theme-splash-small.png)
I absolutely wanna keep the grub splash screen.
Perhaps i made i bit of confusion....

---

### Post by xXx 0wn3d xXx on 2006-06-20
[QUOTE=ralf57]One moment Ramses, i meant ubuntu boot splash
[http://www.simplifiedcomplexity.com/images/screenshots/dapper/flight3/gfxboot-theme-splash-small.png](http://www.simplifiedcomplexity.com/images/screenshots/dapper/flight3/gfxboot-theme-splash-small.png)
I absolutely wanna keep the grub splash screen.
Perhaps i made i bit of confusion....[/QUOTE]
No what he said is to remove the actual boot usplash not the grub or gnome usplash.

---

### Post by Ramses de Norre on 2006-06-20
Ow, ok I got that wrong then.
Uhm best way to do that is installing sysv-rc-conf running it and disabling usplash for your default runlevel (2 if you didn't changed it).

EDIT: I'm wondering myself now, which splash is exactely enabled with the splash option in grub?

---

### Post by ralf57 on 2006-06-20
[QUOTE=xXx 0wn3d xXx]No what he said is to remove the actual boot usplash not the grub or gnome usplash.[/QUOTE]

Thank you xXx 0wn3d xXx,
now it'a all clearer:)

---

### Post by ralf57 on 2006-06-20
[QUOTE=Ramses de Norre]
EDIT: I'm wondering myself now, which splash is exactely enabled with the splash option in grub?[/QUOTE]

Should be anything like this
[http://www.gnome-look.org/content/show.php?content=36907](http://www.gnome-look.org/content/show.php?content=36907)

---

