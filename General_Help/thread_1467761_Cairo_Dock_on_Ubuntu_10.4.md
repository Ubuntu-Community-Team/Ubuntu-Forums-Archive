---
title: "Cairo Dock on Ubuntu 10.4"
date: 2010-05-01
forum: General Help
---

### Post by henrywm on 2010-05-01
I upgraded to Ubuntu 10.4 today. Now the following icons are invisible in Cairo Dock: Show Desktop, Applications, Compiz Icon


The space for those icons still shows, and I can click where the icons would be and access those functions, but the icons themselves are gone. I uninstalled Cairo, rebooted, and then reinstalled. That fixed it, until I booted again. Then the icons were gone again.

---

### Post by fabounet on 2010-05-01
which version of the dock have you now (the Lucid one ?)
also, do youhave this problem in cairo mode ? if so, it may be a problem with your graphic drivers (which card by the way ?).

---

### Post by henrywm on 2010-05-02
Lucid. It was fine until I upgraded to Lucid.

What do you mean by Cairo mode?

---

### Post by fabounet on 2010-05-03
I suggest you (re)install the fglrx drivers (if you have an ATI).
the "cairo" mode is the one without opengl (cairo-dock -c)

---

### Post by henrywm on 2010-05-30
It was using the command "cairo-dock -o -c." I removed the -o (OpenGL). What does OpenGL do?

---

### Post by fabounet on 2010-05-31
-o = opengl = hardware acceleration and 3D
-c = cairo = uses CPU
obviously you can't use both at once ;-)

---

### Post by henrywm on 2010-05-31
The command in my Startup Applications list was copied from one of the launchers installed with the program.

---

### Post by fabounet on 2010-06-02
nope, they have either -c or -o, but not both

---

