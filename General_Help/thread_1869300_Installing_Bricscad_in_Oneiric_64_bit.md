---
title: "Installing Bricscad in Oneiric 64 bit"
date: 2011-10-25
forum: General Help
---

### Post by afde on 2011-10-25
This is what I did to make Bricscad V11 work on Oneiric because of the 
libGL.so not found error:

1)if not installed already, install ia32-libs package from ubuntu software center
2)install 32 bit Bricscad package downloaded from bricsys
3)download mesa deb package for i386 (at this time: libgl1-mesa-glx_7.11-0ubuntu3_i386.deb) and open with archiver
4)extract libGL.so.1 and libGL.so.1.2 to /opt/bricsys/bricscad/v11/ (extract to your home folder and use sudo nautilus command from a terminal to copy the files in graphical mode..) or simply enter sudo cp libGL.so.1* /opt/bricsys/bricscad/v11/ from terminal.
5) enjoy!

I hope that somebody will find this useful!

---

### Post by Gato303co on 2012-01-04
> **afde said:**
> This is what I did to make Bricscad V11 work on Oneiric because of the 
libGL.so not found error:

1)if not installed already, install ia32-libs package from ubuntu software center
2)install 32 bit Bricscad package downloaded from bricsys
3)download mesa deb package for i386 (at this time: libgl1-mesa-glx_7.11-0ubuntu3_i386.deb) and open with archiver
4)extract libGL.so.1 and libGL.so.1.2 to /opt/bricsys/bricscad/v11/ (extract to your home folder and use sudo nautilus command from a terminal to copy the files in graphical mode..) or simply enter sudo cp libGL.so.1* /opt/bricsys/bricscad/v11/ from terminal.
5) enjoy!

I hope that somebody will find this useful!


Hello and thanks for posting this help.

I am afraid it didn't work for me :(

I install ia32, the bricscad deb and copy/paste the libGL files you said, but nothing changed in the output when I open Bricscad :(

---

### Post by Gato303co on 2012-01-04
Here is the output:
```
carlos@carlos-portatil:~$ bricscadv11 
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(bricscad:324:cool:: Gtk-CRITICAL **: IA__gtk_window_resize: assertion `width > 0' failed
Violación de segmento
carlos@carlos-portatil:~$
```Please, would you help me find what am I doing wrong? Thank you

---

