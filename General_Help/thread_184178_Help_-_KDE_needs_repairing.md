---
title: "Help - KDE needs repairing"
date: 2006-05-29
forum: General Help
---

### Post by infoseeker on 2006-05-29
I could not get KDM to work (on entering name and password, system would return to KDM, not start KDE) so I uninstalled it (my bad  :( ). GDM works fine.
Now KDE seems totally unconfigured.  I reinstalled Kubuntu-desktop which seems to have recovered just about everything. A few problems remain tho :

No Multiple desktops in taskbar
No apps running appear in taskbar (example when opening Knetdockapp, message says its already running)
I had to manually add the KDE menu button 
No volume control icon, akregator will not startup...........etc,etc,etc :(.

Any suggestions?

---

### Post by kzutter on 2006-05-29
I am going out on a limb here as my memory is not so good.
I think I deleted my ~/.kde directory before logging into a  KDE session and that did the trick.
If you want to try this you better backup or rename your ~/.kde ( mv ~/.kde ~/.kde-back )

Good luck - let me know how this pans out.

-Ken

---

### Post by infoseeker on 2006-05-29
Sorted out .......thanks.

It was more a matter of adding the correct applet in the right place.  But why would removing/reinstalling KDM have such a huge effect on KDE?

DEPENDENCIES probably ;)

---

