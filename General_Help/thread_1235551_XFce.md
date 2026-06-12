---
title: "XFce"
date: 2009-08-09
forum: General Help
---

### Post by jwkungfu on 2009-08-09
Hi all,

When I first started with Ubuntu (early) 2008, every other day a yellow bulb icon used to show up to let me know of updates waiting...
I don't seem to get that anymore? 


Secondly, I run a crappy old lap-top (slow as a wet week)...
This XFce says that it runs faster and is more simple...

Is it?

Can anybody let me know of any pros/cons...?

And if I do decide to give it a try, how to I switch to it?

Cheers!!

JW.

---

### Post by coldReactive on 2009-08-09
I know one con of xubuntu:

You can't drag menu items from the applications menu to the panel!

---

### Post by Barafu Albino Cheetah on 2009-08-09
XFCE is faster if you use only XFCE and pure GTK/qt/Motiff/...  apps. As soon as you start any app with bindings to KDE or Gnome, the whole subsystems load into memory, and you gain no bonuses anymore. 
And most good apps have bindings. 
Use Gnome, and KDE 3, clean them both from any unneeded things, configure you kernel for lightweight build and high latency. This way you gain more speed, then by switching to XFCE. 
Ubuntu is not the best choice for slow old systems. Look into some distro, where you can install KDE without substantial parts and still have it usable, such as Gentoo. 

P.S. And switch off composing!

---

### Post by martinbaselier on 2009-08-09
I have a pc with gnome, lxde and xfce installed and xfce starts a lot faster than gnome, even with all visual effects off. And when the desktop is loaded fully on gnome, it still takes longer to start firefox than when I'm using xfce. 

xfce is a bit less fancy than gnome or kde, lxde is even lighter. Some gnome panel functions are not available on xfce. 

To install you have two choices:
**sudo apt-get install xubuntu-desktop**
This will install everything that's normally on xubuntu (including all programs that are installed on it) 
 
or 

**sudo apt-get install xfce4**
This will just install xfce4 and you would need to setup the rest manually. Check synaptic afterwards, and search for xfce4 to see which other plugins might be usefull for you. 

When you've installed it, you can choose xfce in your login screen.

---

### Post by Barafu Albino Cheetah on 2009-08-09
Don't speak about firefox - it is a standalone app. Better check the startup speed of k3b and tomboy.

---

### Post by kerry_s on 2009-08-09
> Secondly, I run a crappy old lap-top (slow as a wet week)...

and the specs are?

---

