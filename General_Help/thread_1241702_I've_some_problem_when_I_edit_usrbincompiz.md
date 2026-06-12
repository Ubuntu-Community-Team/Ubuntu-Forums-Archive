---
title: "I've some problem when I edit /usr/bin/compiz"
date: 2009-08-16
forum: General Help
---

### Post by aurora_consurgens on 2009-08-16
when I run this command in Termimal to edit something.  

$ sudo gedit /usr/bin/compiz 

then I saved but it say in terminal 

(gedit:12125): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

what happen? and how to solve this problem. 

Thank you so much for replying 

:):):)

---

### Post by CatKiller on 2009-08-16
I don't know if it's related to whatever problem you're experiencing, but don't use sudo with gedit. Use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") instead.

---

### Post by lessgov2007 on 2009-08-16
One of the easiest ways...

Alt+F2

Type: gksudo nautilus

This will open a nautilus window with administrator privilege. From with the window just navigate to the file you wish to edit, and open it like you normally would. 

Another way, which I find myself often using is nano in the terminal. 

Type: sudo nano /usr/bin/compiz

Or what ever the path is your looking for. 

Nano is a simple terminal editor. Directions are shown at the bottom of the terminal window for operating Nano. Example... Ctrl+O makes it write the changes made. After you press enter confirming your decision. Then Ctrl+X will exit Nano. Very simple, quick, and easy.

---

