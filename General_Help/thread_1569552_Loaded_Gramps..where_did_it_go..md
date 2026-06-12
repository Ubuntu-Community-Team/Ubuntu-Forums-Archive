---
title: "Loaded Gramps..where did it go.?"
date: 2010-09-06
forum: General Help
---

### Post by robertcoulson on 2010-09-06
Hi.. Lately I downloaded a few programs through " Ubuntu Software Center " and I can not find them after the download...The latest one was GRAMPS...Where would it go...Hope some one can give me an idea as to where I can find it.
Robert

---

### Post by t0p on 2010-09-06
A way to locate a program is the **which** command.  If I type into the terminal 

```

t0p@deimos:~$ which gedit
/usr/bin/gedit
t0p@deimos:~$

```

See?  *which* told me that *gedit* (the text editor) is located at /usr/bin/gedit.  If you do the same for *gramps* you may well find it.

If you want to add a new app to the Applications menu, all you need to do is right-click where it says *Applications* and select Edit Menus.  Now you should be able to choose what you want to appear in your menus.

---

### Post by robertcoulson on 2010-09-06
Not to sure about the code you gave me and where to inouy gramps..Also, I looked in the Maim Menu like you said, But I can not see it anywhere, yet it IS installed.
Robert

---

### Post by dFlyer on 2010-09-06
On my Ubuntu 10.04.1 gramps in under Office.

---

### Post by robertcoulson on 2010-09-06
Hi dfyer..I only have 10.04 not 10.04.1..And I could not see it under office...Also, I downloaded lifelines and that is no where to be found...Guess I might as well uninstall them as I can not see or use them..Thanks anyway.
Robert

---

### Post by dFlyer on 2010-09-06
If you have been updating 10.04 regularly, you are running 10.04.1. If you remove gramps, use synaptic package manager, and instead of removing the program, try mark for re-installation.

On another note, I've noticed that sometimes after I install a program with synaptic, I need to logout and log back in to get the program to show up in the menu. With picasa3 I need to reboot before it will show up in the menu so you might want to try these first.

---

### Post by robertcoulson on 2010-09-06
WOW...Dfyer, that WORKED....Thanks very much.
Robert

---

