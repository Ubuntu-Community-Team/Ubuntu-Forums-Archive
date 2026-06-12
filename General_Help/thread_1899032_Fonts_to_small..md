---
title: "Fonts to small."
date: 2011-12-22
forum: General Help
---

### Post by matthewh3 on 2011-12-22
Hi I just installed the Lxde desktop on my Ubuntu11.10 and all the fonts were too small.  I managed to get the menus to a decent size but the panel and program fonts are too small still.  Any help?

---

### Post by MG&amp;TL on 2011-12-22
What size is your monitor? (i.e resolution)

---

### Post by matthewh3 on 2011-12-22
1080p TV.

---

### Post by MG&amp;TL on 2011-12-22
That's the issue.

Gtk (the graphical library behind your windows and stuff) is measured in pixels, not cm. 

Other than decreasing the screen resolution , I've not come up with a solution. What do you generally use your pc for?

---

### Post by matthewh3 on 2011-12-22
A 32" 1080p HDTV as my main monitor.

---

### Post by MG&amp;TL on 2011-12-22
My point being, if you use it as a TV at any point, put up with it, otherwise, decrease the resolution. Sorry I can't help more. Maybe someone else will have a fix.

---

### Post by matthewh3 on 2011-12-22
So I can get the menus fonts to a decent size but not the panels or programs?  Looks like I'll have to use Xfce.  Can anyone else recommend any other lightweight desktops?

---

### Post by SteveDee on 2011-12-23
> **matthewh3 said:**
> ...but the panel and program fonts are too small still...

I'm probably missing your point here, but what happens if you right-click on the panel, select Panel Settings, and increase the "Size Height" & "Icon" settings?

---

### Post by matthewh3 on 2011-12-23
> **SteveDee said:**
> I'm probably missing your point here, but what happens if you right-click on the panel, select Panel Settings, and increase the "Size Height" & "Icon" settings?

I can change the panel and icon sizes but not the fonts within.  Also the fonts in programs like System Monitor are too small.  When I boot from a live USB stick they are all the right size.

---

### Post by cottfcfan on 2011-12-23
You could try installing Ubuntu Tweak.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
You can adjust the font sizes in Tweaks/Fonts.

---

### Post by matthewh3 on 2011-12-23
> **cottfcfan said:**
> You could try installing Ubuntu Tweak.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
You can adjust the font sizes in Tweaks/Fonts.

How come it's not in the official repository?  It didn't work.  Looks like I'll have to use Xfce as a alternative to Unity and Gnome 3.  Or install Lubuntu from disk.  I also had the same problem with the KDE desktop package.

---

### Post by cottfcfan on 2011-12-24
What size are you trying to get your fonts too?
Using Ubuntu Tweak & myunity, or even dconf (its in the repos) you can get your font size upto 1000dpi, which makes each letter about 30cm high.
Works the same in Unity, Gnome Shell, & xfce.

---

### Post by mystika1 on 2011-12-24
Hi,
I am running lxde on my system and I had the same problem as you when I first installed. You must change DPI settings to 110 x 110.  
First..as root gksu leafpad then open and select file system. Make sure that you have a check mark in the box "show hidden files" in the view menu in leafpad or you wont see the proper files. Then choose etc and scroll down to x11 then xorg.conf

You should see a section called Monitor that looks similar to this:

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option   "DPI" "110 x 110"
    Option         "DPMS"
EndSection

You need to add the line
 Option   "DPI" "110 x 110"

like I did above and restart your computer. Your fonts should be much better. Let me know if you have trouble.

Penny

---

### Post by matthewh3 on 2011-12-24
> **mystika1 said:**
> Hi,
I am running lxde on my system and I had the same problem as you when I first installed. You must change DPI settings to 110 x 110.  
First..as root gksu leafpad then open and select file system. Make sure that you have a check mark in the box "show hidden files" in the view menu in leafpad or you wont see the proper files. Then choose etc and scroll down to x11 then xorg.conf

You should see a section called Monitor that looks similar to this:



You need to add the line
 Option   "DPI" "110 x 110"

like I did above and restart your computer. Your fonts should be much better. Let me know if you have trouble.

Penny

Yeah that worked for Lxde and KDE desktops.  The only problem I have now is the fonts on desktop icons in the Lxde desktop are too big and I can't seem to find the settings to reduce them.

---

### Post by mystika1 on 2011-12-24
Maybe this thread from lxde forums would help you.
[http://forum.lxde.org/viewtopic.php?f=21&t=1423&p=3787&hilit=fonts+too+big#p3787](http://forum.lxde.org/viewtopic.php?f=21&t=1423&p=3787&hilit=fonts+too+big#p3787)
Penny

---

### Post by matthewh3 on 2011-12-24
> **mystika1 said:**
> Maybe this thread from lxde forums would help you.
[http://forum.lxde.org/viewtopic.php?f=21&t=1423&p=3787&hilit=fonts+too+big#p3787](http://forum.lxde.org/viewtopic.php?f=21&t=1423&p=3787&hilit=fonts+too+big#p3787)
Penny

The panel any everything else is fine.  It's just on the desktop short-cuts.

---

### Post by matthewh3 on 2011-12-24
I managed to re-reduce the desktop shortcuts fonts by right clicking on the desktop and and choosing desktop settings.  All problems are solved thankyou very much :)

---

