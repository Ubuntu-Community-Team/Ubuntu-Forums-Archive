---
title: "Removed KDE, but theme is still there!"
date: 2009-12-06
forum: General Help
---

### Post by xtjacob on 2009-12-06
I just removed all the KDE applications that were installed after I installed kubuntu-desktop, but in synaptic or any other program run as root all the bars in everything is blue like I still have KDE installed! I think it might have something to do with a theme because I installed one that required the editing of a file beginning with "." in my home folder. Can anyone help?

---

### Post by lidex on 2009-12-06
Press Alt+F2 key combo. In that run dialog enter ```
gksudo nautilus
``` In the nautilus window that appears navigate to "/root/themes" and delete folders pertaining to kde themes. *[COLOR="Red"]Warning - do not mess with anything else as you could bork your entire system!![/COLOR]* Close nautilus immediately and logout/login.

---

