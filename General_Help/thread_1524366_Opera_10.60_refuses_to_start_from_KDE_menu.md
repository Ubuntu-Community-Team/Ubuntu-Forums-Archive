---
title: "Opera 10.60 refuses to start from KDE menu"
date: 2010-07-05
forum: General Help
---

### Post by mister_playboy on 2010-07-05
After upgrading to v10.60, Opera will not run from the KDE menu.  A entry appears in the taskbar and then disappears without opening any window.

The entry for Opera in KDE menu has this command: ```
/usr/bin/opera %u
```
If I open a terminal and type "opera" or navigate to /usr/bin and click on the opera script there, it starts up just fine.

Seems like it should be simple to fix, but I have tried various entries in the KDE menu ("opera", "opera %u", "/usr/bin/opera") and this same behavior occurs with any of them... any help?

---

### Post by shirsch on 2010-07-05
> **mister_playboy said:**
> After upgrading to v10.60, Opera will not run from the KDE menu.  A entry appears in the taskbar and then disappears without opening any window.


Ran into the same thing here.  Found the answer on Linux Questions:  Go into opera:config, search for "trayicon" and disable it.  Quit browser and try again - should work now.

---

### Post by mister_playboy on 2010-07-06
Unfortunately, turning off the tray icon did not solve my problem (although I'm glad they made it easier to do... before it required a CLI switch). :p  I tried renaming my .opera directory to see if my profile was the problem, but the program doesn't even progress far enough to spawn a new directory when opened from the KDE menu.

I'm still baffled as to what the problem is.

---

### Post by ankspo71 on 2010-07-07
Hi,
It is working for me with the default command in the menu:
/usr/bin/opera %U 

Here is an idea or two for you to try: 
```
sh /usr/bin/opera %U
sh /usr/bin/opera

```
Hope that works for you

---

### Post by mister_playboy on 2010-07-07
The problem turns out to have only existed with the Opera entry in KDE's "Favorites" section.  I was editing the Opera entry under Applications > Internet > Opera and I didn't know it was not affecting the entry in Favorites.

I don't see any way to edit the entries in the Favorites list from the menu editor, or to look at what commands the entry in Favorites was calling, but deleting the Favorites entry and then re-adding it solved the problem.

Thanks for the help, everyone.

---

