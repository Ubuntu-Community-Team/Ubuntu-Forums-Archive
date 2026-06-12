---
title: "Gnome-main-menu not showing recent apps"
date: 2010-06-05
forum: General Help
---

### Post by salvador_luna on 2010-06-05
I used to use the gnome-main-menu applet but i noticed that it does not show the recent apps. I looked for something but didn't find anything, but the readme in the package says it needs a patched panel.

Anyone knows anything about it? Do I really need a patched panel? Or just need a gconf setting?

Thanks in advance :)

I forgot! I use ubuntu 10.04

---

### Post by kerry_s on 2010-06-06
works fine for me. shows all the things i opened, tattle tale. :)

---

### Post by salvador_luna on 2010-06-06
> **kerry_s said:**
> works fine for me. shows all the things i opened, tattle tale. :)

Well, the recent documents works fine... in the applications tab, the last applications didn't appear after executing one :), this behavior can be seen in opensuse :)

How did you change the computer icon? overwriting the icon???

Thanks for the replay.

---

### Post by kerry_s on 2010-06-06
in /usr/share/gnome-main-menu/slab-window.glade
use the search-> replace

find: gnome-fs-client
replace: start-here

find: Computer
replace: Menu

if you mess up you can just reinstall "gnome-main-menu" to bring it back to stock, then edit again. (like i just did to grab screenshots for you)

---

### Post by salvador_luna on 2010-06-06
Thanks for the info :)

I'll try to find more info about the recent apps :)

---

