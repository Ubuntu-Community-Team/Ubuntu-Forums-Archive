---
title: "qcad install"
date: 2010-05-31
forum: General Help
---

### Post by jesse c on 2010-05-31
I installed an 'auto cad' program called 'QCad' from the 'applicatons/software center and also checked in the synaptic files and both claim the program is installed but i cant find access to it.I have restarted my computer and looked in all 'application' categories and dont see it
running Lucid 10.4
any body have a better autocad type free program to recommend?

---

### Post by buntudawg on 2010-05-31
Hey

Don't know if this thread will help but someone else had the same problem and it was solved for them. Check ajgreeny's post (#7) esp.

[http://ubuntuforums.org/showthread.php?t=1497848&highlight=qcad](http://ubuntuforums.org/showthread.php?t=1497848&highlight=qcad)

---

### Post by jesse c on 2010-05-31
thanks for trying but that wont help me 'cause i cant even find it to open it from anywhere.I did have it in Karmic applications but i did a clean install from disc to Lucid.

---

### Post by gmargo on 2010-05-31
The qcad package does not supply a *.desktop file that would get it mentioned in the gnome menu.  However, it does provide a "menu" entry file for the alternate menu system.  This whole other menu system can be visible if you install the "menu" and "menu-xdg" packages, then edit your menu (System->Preferences->Main Menu) to included the "Debian" tree.  After your log out/in, qcad will appear in the menu under Applications -> Debian -> Applications -> Science -> Engineering -> QCad.

How did I know the path?  "dpkg -L qcad" shows that the package includes the /usr/share/menu/qcad file, which contains the menu path, underneath the Debian part.

---

### Post by jesse c on 2010-06-01
SOLVED: thanks gmargo that did the trick.It is a very long route to get to the program but it does get me there,and now there are lots of other programs on the debian menue i have to check out.Maybe theres a way to make s short cut directly to QCad i can look into.  JESSE C

---

