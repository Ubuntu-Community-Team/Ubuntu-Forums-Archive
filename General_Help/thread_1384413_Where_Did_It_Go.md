---
title: "Where Did It Go?"
date: 2010-01-18
forum: General Help
---

### Post by carbonbased on 2010-01-18
Using Synaptic Package Manager I installed Smart Boot Manager (SBM), only now I cannot find it. It's not in the Gnome menus and I cannot find where it was placed in the folders.

This is not the first time I've installed something which hasn't shown up in the menus.

What do I need to learn about here?

---

### Post by Xog on 2010-01-18
Places > Find Files

type in Smart Boot 
hit enter

---

### Post by carbonbased on 2010-01-18
> **Xog said:**
> Places > Find Files

type in Smart Boot 
hit enter

O.K.

Results: No Files Found.

---

### Post by oldos2er on 2010-01-18
You can run **dpkg -L sbm** in a terminal to show where each file in the package is. It looks like it's an ncurses (CLI) app, so I'd try running **sbm** in a terminal.

---

### Post by Xog on 2010-01-18
if you used firefox u can go to tools > downloads and run the installer to see if it's already installed. if not install it

if it's already installed try doing another search for "sbm" or follow oldos2er's advice :P

---

### Post by carbonbased on 2010-01-18
> **oldos2er said:**
> You can run **dpkg -L sbm** in a terminal to show where each file in the package is. It looks like it's an ncurses (CLI) app, so I'd try running **sbm** in a terminal.

Thanks. All sub-folders in /usr/share.

---

### Post by louieb on 2010-01-18
I use to put sbm on a floppy disk for use in PCs that could not boot to a cdrom drive. 

Just wondering what you think sbm will do for you. 

If you look at the project page on sourceforge you'll see it hasn't been updated since 2001.

---

### Post by carbonbased on 2010-01-18
> **louieb said:**
> I use to put sbm on a floppy disk for use in PCs that could not boot to a cdrom drive. 

Just wondering what you think sbm will do for you. 

If you look at the project page on sourceforge you'll see it hasn't been updated since 2001.

Just one of several booting options I was looking at to find a way of solving the mangled MBR phenomenon so often seen after an installation.

---

