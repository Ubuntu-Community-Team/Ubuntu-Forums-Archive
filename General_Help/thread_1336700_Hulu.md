---
title: "Hulu"
date: 2009-11-24
forum: General Help
---

### Post by bobbygf on 2009-11-24
I installed Karmic Koala and I can't get Hulu to completely work. When I click on a show, it will start playing, but I can't do **anything** else i.e fullscreen, pause, his res, etc. It actually wasn't a problem until recently. 

Thanks.

---

### Post by wojox on 2009-11-24
What flash version you running:

```
sudo dpkg -l | grep flash
```

---

### Post by winchendonsprings on 2009-11-24
i had the same issue. heres my post on it with the solution

[http://ubuntuforums.org/showthread.php?t=1324591](http://ubuntuforums.org/showthread.php?t=1324591)

---

### Post by bobbygf on 2009-11-25
> **winchendonsprings said:**
> You solved it. This did it -

Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Thats it.

Thanks, this worked perfectly.

---

### Post by n52 on 2009-11-25
I have both KDE and GNOME installed on my system.  I have this same problem on GNOME but everything works fine in KDE.

---

