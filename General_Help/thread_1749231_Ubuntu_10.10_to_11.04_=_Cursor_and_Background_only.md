---
title: "Ubuntu 10.10 to 11.04 = Cursor and Background only"
date: 2011-05-04
forum: General Help
---

### Post by dwbatey on 2011-05-04
I have an eeepc with an Atom n450 and a GMA950 Video...

I have been running 10.10 on it just fine but when I allowed the update manager to upgrade to 11.04... All i get is a background and a cursor, no toolbars. When I right click I get the general context menu to create shortcuts but that is it...
I am able to get to a console using CTRL+ALT+F2 and log in just fine. 

What do I need to do to get my desktop interface back? If this issue has been previously covered in another topic please link it for me.

Thanks in advance.

---

### Post by dwbatey on 2011-05-04
***SOLVED ****
I had to use this command to repair the compiz install

sudo apt-get install compiz

then i rebooted and now I have my desktop.

---

