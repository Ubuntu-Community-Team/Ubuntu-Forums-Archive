---
title: "System -&gt; Preferences -&gt; Appearance Missing"
date: 2010-04-25
forum: General Help
---

### Post by jshendrich on 2010-04-25
I'm running the latest Lucid version.  I just noticed that the Appearance option is missing from System -> Preferences -> Appearance.  I have no idea if it happened during the upgrade but that would certainly be odd.  Does anyone know how to rebuild or add back the Appearance option?

---

### Post by dino99 on 2010-04-25
try into console:

- sudo dpkg-reconfigure gnome-control-center
- sudo dpkg-reconfigure gnome-terminal
- sudo dpkg-reconfigure gnome-media
- sudo dpkg-reconfigure gnome-utils
- sudo dpkg-reconfigure gnome-session
- sudo dpkg-reconfigure gnome-applets-data
- sudo dpkg-reconfigure gnome-panel-data
- sudo dpkg-reconfigure gnome-panel

dont know exactly which one is needed but anyway does not matter

---

### Post by Rubi1200 on 2010-04-25
Have you tried editing the menu to see if it is there? Right click anywhere on the default menu for System and choose Edit menus; maybe it is still there.
Good luck!

---

### Post by jshendrich on 2010-04-25
Thanks for the suggestion.  I ran all the dpkg-reconfigures and got back no errors.  However, I still have the same problem.  I found the Appearance application (through Applications -> Accessories -> Application Finder.  The Appearance application works correctly but it's just not on the correct menu.  Not that big a deal I guess.

---

### Post by Rubi1200 on 2010-04-25
Alternatively, you could run this command which does not require root privileges:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
Just be aware that this will reset ALL custom settings, wallpapers, themes etc. But, it does restore the default settings for the desktop.
Also, in the edit menus option I mentioned above, there is an option to Revert (i.e. restore) the default menus. It might be worth trying that first.
Hope this helps.

---

### Post by jshendrich on 2010-04-25
Rubi1200 - I checked your suggestion but the option isn't there....If I were to add it, what application should the menu option point to?

---

### Post by Rubi1200 on 2010-04-25
I am using Karmic and have not looked at Lucid yet so I don't know if editing menus has changed. It seems a bit odd though that there is no option **in** the menus to restore default settings. Sorry I can't help you further there. If you can live with the fact that the option is somewhere else, then I suppose it is ok. Otherwise, you might want to consider a clean install when the final version comes out in a few days.

---

### Post by Dareth on 2010-04-25
Try going to System -> Preferences -> Main Menu. Then navigate to System -> Preferences and make sure the Appearance application is checked.

---

### Post by jshendrich on 2010-04-25
I found a way around.  I edited the menu and searched for the application which I found in /usr/bin/gnome-appearance-properties.

Thanks for everyone's help and suggestions!

---

### Post by Rubi1200 on 2010-04-25
Excellent!
:)

---

