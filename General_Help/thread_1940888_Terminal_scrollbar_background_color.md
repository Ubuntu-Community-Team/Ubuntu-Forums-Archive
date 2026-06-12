---
title: "Terminal scrollbar background color"
date: 2012-03-14
forum: General Help
---

### Post by brainwash on 2012-03-14
Hello,

does anyone know how to change the background color of the xfce4-terminal scrollbar?

After changing the bg color of the terminal (edit > preferences > colors) I also want to change the scrollbar bg color to fit the new look. The black background seems to be terminal only, other windows got a gray-ish scrollbar bg color.

Many thanks
brainwash

---

### Post by LewisTM on 2012-03-14
The color of scrollbars, menus, buttons, etc. are all determined by your current theme, which is found under Appearance/Style in the Settings Manager. More can be added with the xfwm4-themes package. To change individual elements you might have to manually edit the theme config files.

You could also try the overlay scrollbar style by installing package overlay-scrollbar. That provides a popup scrollbar with a small footprint that blends with the window background.

Cheers!

---

### Post by brainwash on 2012-03-14
Thanks for your hint. :)

So I checked the theme config files and there is indeed a special file for the terminal appearance:

/usr/share/themes/greybird/gtk-2.0/apps/terminal.rc

The overlay-scrollbar looks interesting too. I'll install the package later to get an impression of this concept.

---

### Post by vasa1 on 2012-08-09
> **brainwash said:**
> ...
The overlay-scrollbar looks interesting too. I'll install the package later to get an impression of this concept.
Just thought I'd "poke" this thread :)

Did you go for the overlay scrollbars? I have them by default because I installed Xfce 4.10 on top of Ubuntu 12.04 and quite like them.

---

### Post by brainwash on 2012-08-11
> **vasa1 said:**
> Did you go for the overlay scrollbars? I have them by default because I installed Xfce 4.10 on top of Ubuntu 12.04 and quite like them.
I really don't dislike any of the major desktop environments, even the new tablet-oriented ones, but I prefer having normal scrollbars.

---

