---
title: "Wine Fonts and Half Life 2"
date: 2009-09-11
forum: General Help
---

### Post by mikeym on 2009-09-11
Hi,

I'm playing half life 2 again and I've got most of it working but there are still a couple of weird font issues. The Loading... caption at the top of the progress bar doesn't seem to display properly. And in-game the italic captions don't display properly at all. 

I've already installed ttf-mscorefonts-installer, copied the following fonts to ~/.wine/drive_c/windows/Fonts and [installed subpixel shading]("http://www.wine-reviews.net/wine-reviews/tips-n-tricks/how-to-enable-font-anti-aliasing-in-wine.html"). 

```
Arial.TTF
Arialbd.TTF
Arialbi.TTF
Ariali.TTF
AriBlk.TTF
cour.ttf
courbd.ttf
courbi.ttf
couri.ttf
jester.TTF
Lucida Grande.ttf
l_10646.ttf
TAHOMA.TTF
tahoma.ttf
Times.TTF
Timesbd.TTF
Timesbi.TTF
Timesi.TTF
Trebuc.TTF
Trebucbd.TTF
Trebucbi.TTF
Trebucit.TTF
Verdana.TTF
Verdanab.TTF
Verdanai.TTF
Verdanaz.TTF
```

So does anyone know what font I'm missing?

---

### Post by XCan on 2009-09-11
I dunno if this will help, but I never used your approach to copy the fonts like that, instead I've always use winetricks to install "corefonts". [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) If there are no differences between the fonts, of course it won't help you, but can't hurt to try. :)

---

