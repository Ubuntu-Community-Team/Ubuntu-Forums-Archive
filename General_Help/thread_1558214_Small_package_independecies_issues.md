---
title: "Small package independecies issues"
date: 2010-08-21
forum: General Help
---

### Post by ALF102 on 2010-08-21
From the terminal I got this message:

The following packages were automatically installed and are no longer required:
  libqt4-opengl freemat freemat-help libgfortran3 libsdl-ttf2.0-0
  libmikmod2 libqt4-svg libblas3gf libamd2.2.0 libsdl-mixer1.2
  libumfpack5.4.0 freemat-data libsmpeg0

Ok, what I really don't understand is that why is it that Freemat, my most important software, is listed as "no longer required"? 
Of course if I use sudo apt-get autoremove will remove all the mentioned packages including Freemat.

---

### Post by Pollox on 2010-08-22
Perhaps you installed some other program that depended on freemat, like a plugin or a gui for it?  If you open up Synaptic, find freemat, click the package menu, and uncheck "Automatically installed", it should remove it from the autoremovable list.  There should be a way to do this using apt from terminal, but I don't know the command.

---

### Post by ALF102 on 2010-08-22
ok done. Its gone from the auto remove list

---

