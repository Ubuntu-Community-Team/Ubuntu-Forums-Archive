---
title: "KDE and Gnome"
date: 2009-08-09
forum: General Help
---

### Post by toleolu on 2009-08-09
Is there any difference between these two other than basically what you see on the screen?? From what I've read they seem to pretty much be just desktop environment programs. (If that's the right word)

The reason I ask is that I've been playing around with Kdenlive and I've noticed that when it crashes, I see that prompt on the bottom of the screen about "Launching Knotify.." something like that. (From what I've read, that appears to be something like the old Windows deal of reporting an error.)

The kdenlive seems a little buggy, I was just wondering if that might have anything to do with any differences between Gnome and KDE. I'm using Gnome now.

Ubuntu 9.0.4 and Kdenlive 0.7.4

Thanks

---

### Post by zvacet on 2009-08-09
> From what I've read they seem to pretty much be just desktop environment programs.

That is correct.I don´t use KDE so I can nor tell you about bugs.Use one witch is better for you or easier to use.

---

### Post by ibutho on 2009-08-09
KDE and GNOME are Desktop Environments which use different toolkits and have very different ideas when it comes to developing a DE. If a KDE app crashes, then knotify is launced. It is a tool used by KDE apps to tell you that something has gone wrong somewhere. I don't think the bugs in Knotify have anything with it being a KDE app (I don't think its even an official KDE app). I use KDE apps in GNOME and vice versa and they usually just work.

---

### Post by JC Cheloven on 2009-08-09
AFAIK Gnome is built using GTK, and KDE using QT. These are graphic libraries and toolkits. Apart from some minor desktop utilities (as knotify is), the differences occur behind the scenes: when you install for the first time an application intended for KDE under Gnome, or vice versa, usually a bunch of dependencies are installed (apt cares of that) so that the missing QT -or GTK- libraries are present for the new program to use them. More disk space is used, but it's  cheap nowadays...

Also because of the graphic toolkits used, some apps may look sligtly different under gnome and kde.

---

