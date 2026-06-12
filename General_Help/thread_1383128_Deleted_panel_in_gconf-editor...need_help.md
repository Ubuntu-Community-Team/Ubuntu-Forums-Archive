---
title: "Deleted /panel/ in gconf-editor...need help"
date: 2010-01-16
forum: General Help
---

### Post by j.karmann on 2010-01-16
i downloaded cairo-dock and wanted my top panel to go away. i read on some other post to go into gconf-editor, and i'm not completely sure, but, apps>panel>something else....i didn't pay to much attention....sorry...anyways, i want it back, and i just want to hide it with a really long delay which i can do no problem...i just need help getting it back....thanks, and i'll stop doing retarded stuff from now on

---

### Post by drs305 on 2010-01-16
If you deleted it, to add a top panel, right click on the bottom panel, New Panel, then right click on the new one, Properties, and use the Orientation setting to put it where you want.

---

### Post by j.karmann on 2010-01-16
the is no bottom panel. i right-clicked and deleted the bottom...then i went to gconf-editor to delete the other...alot of other post say it cant be "deleted" only hidden...but its gone

---

### Post by drs305 on 2010-01-16
Just run this command. It will move your current panel settings folder to the Desktop. Logout and then log back in and a default panel setup will be regained.
```
mv $HOME/.gconf/apps/panel $HOME/Desktop/old-panel
```

---

### Post by j.karmann on 2010-01-16
just did that...it did save the folder to the desktop...logged out and back in...folder still there...panel still not

---

### Post by drs305 on 2010-01-16
Was a new ~/.gconf/apps/panel folder created? Normally that is all you have to do to recreate a new default panel. ( ~/ is a shortcut for /home/yourusername)

Have you uninstalled cairo dock - or do you still want it? I've never used it so I don't know whether it can be interfering with the normal gnome panels. 

Perhaps you can figure out what you changed in gconf-editor by exploring the settings:
```

gconf-editor /apps/panel

```

---

### Post by j.karmann on 2010-01-16
there isn't a panel folder in ~/.gconf/apps....but looking at gconf-editor, it appears like it should (in my opinion), i can go to apps/panel and see default setup, toplevels, top and bottom panels, objects, etc....no hide options are checked, like i said it appears to be there and ok...but no pysical folder at that location

---

### Post by j.karmann on 2010-01-16
ok...i typed 'gnome-panel' in terminal and it showed up...top and bottom....and now there is a panel folder in there...maybe it just didn't run automatically after the restart

---

### Post by j.karmann on 2010-01-16
thanks for your help...i'm just auto hiding it, hides in 5 ms, unhides in 5000 ms, and only 1 pixel visible...cant see any part of it at all and the mouse has to sit there quite a while before it drops...thanks again

---

