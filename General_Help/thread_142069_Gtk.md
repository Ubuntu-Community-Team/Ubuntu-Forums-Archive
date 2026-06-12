---
title: "Gtk"
date: 2006-03-09
forum: General Help
---

### Post by harley on 2006-03-09
im trying to install a new program it is saying i do not have GTK installed what is the best wat to install it by typeing sudo apt-get install gtk but it say it can not find that package did i type the code wrong?

---

### Post by ComplexNumber on 2006-03-09
if you are running ubuntu, you must have gtk installed. the reason why its telling you that you haven't got gtk installed is because you haven't got the devel package (ie gtk2-devel) installed. when you install that, it puts a file called gtk2.pc(or something similar) in the pkgconfig directory in /usr/lib. when the system is looking for dependencies or you are compiling a package from source, the system looks in /usr/lib/pkgconfig and /usr/local/lib/pkgconfig to see if it can find the package that it depends upon.

---

### Post by lamego on 2006-03-09
Look for the package libgtk2.x.x on the package manager and install it.

---

### Post by harley on 2006-03-09
what is the best way to uninstall the old version of GLIB and install the new one as i have an older version and wish to update

---

