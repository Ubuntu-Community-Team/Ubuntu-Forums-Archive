---
title: "change screensaver pictures folder"
date: 2009-09-14
forum: General Help
---

### Post by charonred on 2009-09-14
I want screensaver to use a folder other than 'Pictures' for its photo source, but can't find an option for that.

How do I get the screensaver to access other folders, or is there a replacement screensaver application for the standard Gnome one in Ubuntu 8.04

---

### Post by Vaphell on 2009-09-14
quick googling indicates that the gnome devs thought people don't need to configure their screensavers and you have Pictures dir set by default.
You can hack it by changing default pix dir path somewhere in gnome configs, but it's an ugly solution and you should find some other screensaver app if you want config panels.

---

### Post by charonred on 2009-09-15
thanks,

I expected a 'Browse' option like Windows has; it's a minor bug, but like many others I suspect, I want to be able to change photo folders when I get bored of the same screensaver images; and all without having to do an 'ugly hack' of the configuration file each I want to change folders, or changing the contents of the 'Pictures' folder.

Hopefully there's a ready made screensaver app out there.

---

### Post by Lessss on 2009-11-11
Instead I selected in the screen saver to use F-spot photos. Then in Fspot I imported the drive folder location and it imported all the picture locations ( not the pics).  When I want to add a photo, I open Fspot and drag the photo into fspot and it creates a new link.  It took a while to import my 20,000 pics but it didn't crash the screen saver like the other methods I tried.

---

### Post by wdeutschman on 2011-02-22
Changing the default pictures location is pretty easy. Just edit /usr/share/applications/screensavers/personal-slideshow.desktop

Several lines in, it has:

Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow

Add on the end so it reads:

Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=yourpicturesfolder

Where"yourpicturesfolder" is wherever you want the screensaver to look.

Done.

---

### Post by ahalin on 2012-03-10
Just to clarify:

Open a terminal
```
ctrl+alt+t
```
Edit *personal-slideshow.desktop* as root:

```
gksudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop
```

(replace gedit with your notepad program)

and add
```
 --location=yourpicturesfolder
``` 

(where"yourpicturesfolder" is wherever you want the screensaver to look) to the end of the line *Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow* (do not add a complete new line!!). Save/exit *personal-slideshow.desktop*.

Works a treat in Linux Mint 11 (Gnome) and, happily, solved an issue I had with TWO screensavers running at once.  :D

---

