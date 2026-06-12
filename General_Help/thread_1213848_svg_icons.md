---
title: "svg icons??"
date: 2009-07-15
forum: General Help
---

### Post by abhilashm86 on 2009-07-15
i need icons for file,open,cut and more kinda applications,
i'm doing a project where i need to use these icons for GUI, so anyone knowing about svg can give me links to browse and download, 
i did a quick search and found more png, so asking here for quick help........

---

### Post by niteshifter on 2009-07-15
Hi,

You probably already have them. Look in /usr/share/icons/gnome/scalable and /usr/share/icons/gnome-alternative/scalable

---

### Post by CatKiller on 2009-07-15
They are GTK theme-dependent. So you probably already have many. If you're using GTK+ to create your GUI you probably don't want to specify a particular file anyway; you'll want to leave that to the rendering engine so that it remains theme-dependent for the users of your application.

If you want a set of icons that will fit in with most others, the Tango Project icons are quite nice. You've probably got those already, too.

---

### Post by abhilashm86 on 2009-07-16
> **CatKiller said:**
> They are GTK theme-dependent. So you probably already have many. If you're using GTK+ to create your GUI you probably don't want to specify a particular file anyway; you'll want to leave that to the rendering engine so that it remains theme-dependent for the users of your application.

If you want a set of icons that will fit in with most others, the Tango Project icons are quite nice. You've probably got those already, too.

oh yes now i get point, but i'm doing GUI using Qt, will the render machine will assign icons?? 
we need to specify the icon svg path right??

---

### Post by CatKiller on 2009-07-16
> **abhilashm86 said:**
> oh yes now i get point, but i'm doing GUI using Qt, will the render machine will assign icons?? 
we need to specify the icon svg path right??

I have no idea. I've not done GUI development (using Qt or otherwise). The icons are the same though, following freedesktop.org's icon specification. I'd imagine that you would still want to only specify the generic name rather than the full path, though, so that KDE themes still work.

---

### Post by abhilashm86 on 2009-07-16
> **CatKiller said:**
> I have no idea. I've not done GUI development (using Qt or otherwise). The icons are the same though, following freedesktop.org's icon specification. I'd imagine that you would still want to only specify the generic name rather than the full path, though, so that KDE themes still work.

fine, now i saw few examples in trolltech, i made a file called images and called them in Qt, works fine,
yes in /usr/share/icons/Humans, i got lots of good .svg icons, problem solved!!!

---

