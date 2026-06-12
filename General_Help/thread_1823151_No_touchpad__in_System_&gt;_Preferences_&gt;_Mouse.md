---
title: "No touchpad  in System &gt; Preferences &gt; Mouse"
date: 2011-08-11
forum: General Help
---

### Post by pain.reign on 2011-08-11
**Disabling Touchpad while Typing**

 Go  to System > Preferences > Mouse > Touchpad and uncheck 'Disable  touchpad while typing' and 'Enable mouse clicks with touchpad"

I don't have touchpad there what to do?

---

### Post by Carborundum on 2011-08-11
First thing that comes to mind:

```
sudo apt-get install xserver-xorg-input-synaptics
```

Try that. If it is already installed, I don't know.

---

### Post by ajgreeny on 2011-08-11
Also try adding gpointing-device-settings.  That gives you a gui to set the mouse and trackpad.

You can also use **synclient** command to change the configuration in the cli.  ```
synclient -l
``` shows all the available options and current settings, and you can play around with the settings to make changes, eg ```
synclient MaxTapTime=0
``` will turn off "tap-to-click"

---

### Post by pain.reign on 2011-08-11
Thnx all here is what i get:

sudo apt-get install xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
The following package was automatically installed and is no longer required:
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

As u see it says no synaptics loaded though its installed.

About gpointing-device-settings it doesn't give any options like disabling while typeing etc. It has only one option called "use middle button emulation".

So what to do?

---

### Post by pain.reign on 2011-08-13
Can anyone help?

---

### Post by Carborundum on 2011-08-13
Try installing gpointing-device-settings. It should be able to configure touchpad behavior.

---

### Post by pain.reign on 2011-08-13
Its installed see my posts ... it doesn't help to disable touchpad while typeing. And doesn't cover all options covered in mouse-> touchpad menu.

---

