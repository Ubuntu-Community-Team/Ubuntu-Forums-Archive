---
title: "It won't let me go to dual Monitors?!"
date: 2009-09-26
forum: General Help
---

### Post by Bluehotdog5 on 2009-09-26
I love ubuntu but the only thing I dislike about it is that whenever I install, there's something complicated that goes wrong. This time is the dual monitor display.
I went to NVIDIA X Server settings and tried "Separate X Screen" and "apply" and got this message:

"The surrent settings cannot be applied for one or more of the following reasons
-the location of an X screen has changed
-the location type of an X screen has changed
-the color depth of an X screen has changed
-an X screen has been added or removed
-Xinerama is being enabled/disabled
for all the requeste settings to take effect, you must save the configuration to the X config file and restart the X server"

so I click "Save to X configuration file" and I get this
"unable to create new X config backup file'/etc/X11/xorg.conf.backup'"

It's so aggravating!!!!!!

---

### Post by chinaCat86 on 2009-09-26
try using twin view instead of Separate X Screen?

---

### Post by Bluehotdog5 on 2009-09-26
Thanks! it works but I still can't save to a xorg.conf file to save the configuration. (the settings revert when I reboot)
How do I write permmisions so I can save the config?

---

### Post by gordintoronto on 2009-09-26
From a terminal session:

sudo [program name]

---

### Post by Johnny B on 2009-09-27
you have to open nvidia-settings with sudo privileges
you can enter it by pressing alt-F2 and type 'sudo nvidia-settings'
then you will be able to save it

---

### Post by SilverShadow118 on 2009-09-27
did you enable dual monitors in bios?

---

### Post by CatKiller on 2009-09-27
[**gksudo**]("http://www.psychocats.net/ubuntu/graphicalsudo") nvidia-settings

Don't use sudo for graphical applications.

---

### Post by scouser73 on 2009-09-27
Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

