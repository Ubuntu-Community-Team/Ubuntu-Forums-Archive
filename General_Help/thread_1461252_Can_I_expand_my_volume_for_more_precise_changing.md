---
title: "Can I expand my volume for more precise changing?"
date: 2010-04-24
forum: General Help
---

### Post by jeremyleroy96 on 2010-04-24
I want to edit my volume meter so that way i can change my volume but be more precise about it. I mean if i slightly slide my finger a little bit it goes from to mute to all the way up. (I have a touchpad buttons)

---

### Post by towheedm on 2010-04-28
Since you did not say what version of ubuntu, I'll assume it's Karmic.
The sensitivity of the volume control is set by the **volume_step** key in the gconf database.  It's value can be from 1 to 100.  The lower the number, the least sensitive the setting.  To check the present setting, enter the following command in a terminal window:
```
gconftool-2 --get /apps/gnome_settings_daemon/volume_step
```To change the setting, enter (replace [COLOR=Red]value[/COLOR] with a number from 1 to 100):
```
gconftool-2 --type int --set /apps/gnome_settings_daemon/volume_step [COLOR=Red]value[/COLOR]
```If you are more comfortable with a GUI, open the gconf configuration editor:
```
gconf-editor
```On the left pane, double click on **apps** and then on **gnome_setting_daemon**.  On the right pane, double-click on **volume_step** and enter the new setting in the [COLOR=Red]Edit Key[/COLOR] dialog.

Hope this helps.

---

### Post by warfacegod on 2010-04-28
FYI: It defaults at 6 (for what ever stupid reason).

You might consider creating a keyboard shortcut for the master volume.

---

