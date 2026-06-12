---
title: "epsxe help!!"
date: 2009-11-09
forum: General Help
---

### Post by Dreamer8001 on 2009-11-09
Ok, I'm running ubuntu 9.10(Karmic Koala) and installed expse 1.6.0 and all the plugins it needed according to this site: [http://www.mepisguides.com/playstation/ePSXe-install-Part-1.html](http://www.mepisguides.com/playstation/ePSXe-install-Part-1.html). I follow all the steps there but couldn't run it in the terminal or just by clicking the binary file (epsxe) itself. In the terminal it display "Killed", and when clicking on the binary epsxe file nothing happens.
[COLOR=White].[/COLOR]
The output on the terminal shows:
[COLOR=White].[/COLOR]
la@Ubuntu:~/epsxe$ ./epsxe
Killed
[COLOR=White].[/COLOR]
Anyone has an idea on whats going on? I'm completely lost.

---

### Post by Dreamer8001 on 2009-11-09
Ok, I don't know what I did but now in the terminal it shows :
[COLOR=White].[/COLOR]
la@Ubuntu:~/epsxe$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
la@Ubuntu:~/epsxe$
[COLOR=White].[/COLOR]
Seems like it missing **libgtk-1.2.so.0**, anyone know how to fix this?

---

### Post by darolu on 2009-11-13
**If** you are running 64-bit Ubuntu you will need to manually install these 32-bit libraries: ncurses gtk1.2 glib1.2. You can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) you'll need to extract the .deb files, do **not** install normally or with getlib, extract with dpkg-deb --extract filename.deb /home/(user)/(whatever) and then mv the libgdk-1.2.so.0.9.1 and libglib-1.2.so.0 to /usr/lib32/
The ncurses library is easier as there is 32-bit version of it for 64-bit Ubuntu so you can install it normally: [http://packages.ubuntu.com/karmic/lib32ncurses5](http://packages.ubuntu.com/karmic/lib32ncurses5) [http://packages.ubuntu.com/karmic/lib32ncurses5-dev](http://packages.ubuntu.com/karmic/lib32ncurses5-dev)

If you are running 32-bit Ubuntu and still have the problem, means Karmic comes with 2.0 and epsxe needs 1.2, install it normally.

---

