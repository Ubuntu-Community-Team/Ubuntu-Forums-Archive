---
title: "Broken Wine Links"
date: 2011-03-15
forum: General Help
---

### Post by Shadowgamon on 2011-03-15
After using Ubuntu for some time, I became accustomed to the native apps, and soon lost interest in my "indispensable" windows apps. So to save space I un-installed them all from within wine. However, persistent are the links to said apps (either a specific like Microsoft Word 2007 or more commonly "A Wine Application" is seen whenever the system I've tried deleting the .Wine Folder, as well as all the other places I could find it in /home. But the links remain , after 5 re-installations, upgrades, reverts, and distro changes, leading me to believe the problem still lies within the recesses of the home folder(on a separate partition) . Any Suggestions on doing this without completely wiping my profile?

---

### Post by grahammechanical on 2011-03-15
I think I know what you are referring to. I have un-installed programs from inside wine but the name still remains in the wine menu or sub-menu. If this is your problem, then this is what you do. I have only just discovered it by looking in the help documentation.

Right click Applications and select Edit Menus. Go down the list of menu items until you come to the wine entry. Expand the wine item and then the Programs item and so on until you come to the program that you have un-installed. In the right hand column remove the tick mark in the box labeled Show. That should do it.

Regards.

---

