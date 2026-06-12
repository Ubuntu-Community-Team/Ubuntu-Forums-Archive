---
title: "Nautilus launches twice in 11.10 Gnome Classic"
date: 2011-11-20
forum: General Help
---

### Post by 73ckn797 on 2011-11-20
Running 11.10 Gnome Classic. When I go to Places and select any folder, Nautilus will load twice. No sure what to do about this. It does not matter what folder I choose.

When running Gnome, many apps are listed twice. See attached image.

What could be causing this?

---

### Post by LinuxFan999 on 2011-11-20
> **73ckn797 said:**
> Running 11.10 Gnome Classic. When I go to Places and select any folder, Nautilus will load twice. No sure what to do about this. It does not matter what folder I choose.

When running Gnome, many apps are listed twice. See attached image.

What could be causing this?
First, it's called Gnome Shell, not Gnome classic. Second, I have never heard of such an issue, and I don't use Gnome Shell, so I cannot help you right now.

EDIT: I also noticed that some apps are listed once, one 3 times, and 4 listed twice.

---

### Post by 73ckn797 on 2011-11-21
> **LinuxFan999 said:**
> First, it's called Gnome Shell, not Gnome classic. Second, I have never heard of such an issue, and I don't use Gnome Shell, so I cannot help you right now.

EDIT: I also noticed that some apps are listed once, one 3 times, and 4 listed twice.

I know what it is called and I am running it as Gnome Classic. Your post does not help one bit.

---

### Post by Frogs Hair on 2011-11-21
Hi 73ckn797  

The screen shot in your first post is the application view in the Gnome Shell , So I am confused as to what desktop environment you need Help with .

One thing you could try would be to reset Gnome from the command prompt . Open the keyboard settings , proceed to shortcuts > system > show run the command prompt . Set Alt + F2 as the shortcut .

Close all programs , open the command prompt with the new short cut and enter ```
r
``` OR ```
reset
``` If that fails try the following if you are logged into the Gnome Shell , which appears as _Gnome_ in the login session list . ```
gnome-shell --replace
``` 

Gnome Shell cheat sheet : [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by 73ckn797 on 2011-11-21
[QUOTE=Frogs Hair;11478275]The screen shot in your first post is the application view in the Gnome Shell , So I am confused as to what desktop environment you need Help with ./QUOTE]

There are 2 issues. The screenshot is Gnome shell. The Nautilus issue is when I am running in the Gnome Classic mode. I will mostly be using the Classic.

I figure since I am test driving 11.10 with Gnome shell that it will mature in time. The install will not be used once 12.04 is released. Then I will likely replace 10.04 with the latest LTS.

---

### Post by 73ckn797 on 2011-11-23
SOLVED!
I installed Gnome Shell and the gnome fall back. The double menu entries when running Gnome Shell, not Gnome Classic, and the double loading of Nautilus are solved.
The solution was found when running Main Menu. There is an entry for Debian. Under that item were all apps under their varying sub-menus. By unchecking all entries the double icons and Nautilus issue has stopped. The system will not allow me do delete the Debian or sub-menu categories however.

---

