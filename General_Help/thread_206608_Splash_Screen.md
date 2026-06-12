---
title: "Splash Screen"
date: 2006-06-30
forum: General Help
---

### Post by treehopper29 on 2006-06-30
What is the easiest way to change the spalsh screen.

---

### Post by mbeierl on 2006-06-30
Are you talking about the background for grub or the boot time messages background screen?

---

### Post by joshrobinson on 2006-06-30
[QUOTE=mbeierl]Are you talking about the background for grub or the boot time messages background screen?[/QUOTE]

ive never had any luck changing the boot time screen personally.. it always gets messed up and i have no splash at all.. so right now i just have the vga set on it, and in verbose with no quiet mode

but the splashscreen after you login can be changed if you use gnome with gnome splashscreen manager.. just install gnome-art and it should install with it

for kde i have no idea

---

### Post by mbeierl on 2006-06-30
Ah, that's true - there is a third "splash screen".  So to identify them (in chronological order :) )

[LIST=1]
[*]The boot menu (grub) where you highlight the kernel you want booted.  (this is the bootsplash)
[*]The background image and text colours for the boot progress messages (this is usplash)
[*]The graphical login background.  (this is controlled by gnome or kde)
[/LIST]

Searching on the terms above should help you figure out how to make them work.  As for me, I have personally customized both my grub bootsplash and my boot progress usplash, so I can help with either of those.

---

### Post by Jucato on 2006-06-30
mbeiler, just a little correction. 

- The bootsplash is the splash screen that you see when Linux is loading, the one with scrolling lines. 
- Usplash is the Ubuntu bootsplash program. 
- The splash screen is the animated screen that you see when loading GNOME or KDE. This usually displays messages like loading peripherals, loading the desktop, etc. In KDE, the program that handles this is KSplash. I'm not sure what it is called in GNOME.
- GRUB Splash is the name of the GRUB background image
- the graphical login manager background is not a splash screen. It's a background. It is handled by GDM in GNOME and KDM in KDE.

To change the splash screen (the one you see while loading GNOME) in GNOME, you can also follow this: [http://art.gnome.org/faq.php#q8](http://art.gnome.org/faq.php#q8). In KDE, you can install new themes from kde-look.org through the Splash Screen control center module (in System Settings).

References:
[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/) 
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)
[http://www.bootsplash.org/](http://www.bootsplash.org/)
[http://docs.kde.org/stable/en/kdebase/ksplashml/introduction.html](http://docs.kde.org/stable/en/kdebase/ksplashml/introduction.html)

---

