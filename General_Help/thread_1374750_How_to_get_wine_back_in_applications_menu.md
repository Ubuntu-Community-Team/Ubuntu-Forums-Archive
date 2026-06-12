---
title: "How to get wine back in applications menu?"
date: 2010-01-07
forum: General Help
---

### Post by bruno9779 on 2010-01-07
I have tried installing logmein in wine.
It installed fine, but didn't work so I removed it. Its icons though, would not be deleted so I removed Wine entry in "Edit menus".

after this I purged wine, deleted /.wine and reinstalled, but the menu entries do not get reinstalled.

I know how to make launchers, what I want is the interactive menus back (browse c, uninstall and programs)

---

### Post by Confirmed on 2010-01-07
Hi bruno!

1.) sudo apt-get purge wine

2.) rm -rf $HOME/.local/share/applications/wine
3.) rm -rf $HOME/.wine

4.) System wide application icons usually get placed in /usr/share/applications 

The .desktop files in these folders hold the configuration for the icons. There can also be a png file (icon image) that goes along with it.

5.) Open ~/.config/menus/applications.menu in your favorite text editor and search for the following:
Code:
<Name>wine-wine</Name>
<Deleted/>
Remove the <Deleted/> tag and the wine menu should reappear in your applications menu. You can also delete everything in the file pertaining to wine for a fresh, but complete reinstall

---

### Post by bruno9779 on 2010-01-07
Thanks

Just what I needed

---

