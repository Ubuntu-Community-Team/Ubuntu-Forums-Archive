---
title: "GTK1 fonts are still huge"
date: 2005-02-20
forum: General Help
---

### Post by NeoChaosX on 2005-02-20
Can anybody help me with the huge fonts being used in GTK1 apps? I've tried both gtk-theme-switch, adding a .gtkrc.mine file in my home folder and following the instructions in [this](http://www.ubuntuforums.org/showthread.php?t=6921) thread, but the menus in MPlayer and XMMS are still the same ugly, huge fonts. I'd love to know if there's anything I missed. Using Warty.

---

### Post by kassetra on 2005-02-20
Ohhh my. The reason it's making them so big is because it's trying very hard to use nice fonts and anti-alias them, but it no longer has all the utilities to do so (they've been updated/converted to gtk2), so... gtk1 fonts are a mess, and trying to make them nicer usually ends up messing gtk2. But here are some suggestions that won't mess up your gtk2:
     
     1. Have you installed mplayer-fonts?  That might help you out quite a bit.
 2. there is a replacement for xmms that is gtk2 compliant and that works near exactly like xmms and uses the same skins & plugins... it's called beep-media-player. I just myself switched from xmms to bmp because of the whole fonts issue.
     
 Now, I know that's not what you were hoping for, so let me direct you to the fun that is making gtk1 and gtk2 fonts play nicely together: 
     
     [color=Red]WARNING!  These suggestions could mess up your gtk2 fonts!![/color]
     
     First, try this system-wide fix:
      ```
sudo ln -s /usr/share/themes/FAVORITE_THEME_GTK2/gtk-1.0/gtkrc /etc/gtk/gtkrc
``` 
     
     If that fails, here is the long, arduous process:
     1. Download and compile gdkxft ([http://gdkxft.sourceforge.net/]("http://gdkxft.sourceforge.net/")) 
   2. In order to have fonts play nicely for gtk 1.x apps and gtk 2.x apps at the same time, the gtk 1.x apps either: 
  (a) have to be recompiled to link to libgdkxft.so or 
  (b) you have to start it with a wrapper script to preload the lib, example:
   ```
#!/bin/sh 
              export LD_PRELOAD=/usr/local/lib/gdkxft.so 
              command_to_start_xmms
```
     
     I hope this helps you.  Sorry I don't have any better answers.

---

### Post by istoyanov on 2005-02-20
If you've applied the mentioned customization to .gtkrc.mine, the value in "Desktop preferences -> Font -> Details -> Resolution" should be the same as shown by the command "xdpyinfo | grep resolution".

HTH!

---

### Post by NeoChaosX on 2005-02-20
Trying Beep now, works great. MPlayer in general is driving me nuts, so I'm thinking of removing it instead of bothering with the damn program.  ](*,)

Besides, I don't want to take a risk by breaking my GTK2 fonts. Still, thanks for the suggestions.

---

### Post by kassetra on 2005-02-20
I went from mplayer to gxine, and gxine works fine... so maybe you want to try that instead?

---

### Post by NeoChaosX on 2005-02-20
And gxine is nice...much thanks again kass!  :-)

---

### Post by kassetra on 2005-02-20
you're welcome!  :)

---

### Post by piedamaro on 2005-02-20
gtk2 apps will segfault if gdkxft is preloaded. 
The trick in .gtkrc.mine should work, but if not, you can edit your /etc/X11/XFree86.conf and swap the lines where it says 100dpi and 75dpi like this:

        FontPath        "/usr/lib/X11/fonts/75dpi/"
        FontPath        "/usr/lib/X11/fonts/100dpi/"

---

