---
title: "Gnome-desktop broken after installing some software"
date: 2010-11-29
forum: General Help
---

### Post by Jamesss on 2010-11-29
I've recently had a problem in Pure Data which required installing some other software via the CLI (gavl and gmerlin). I managed to install some of these, but on rebooting I get lots of error messages:

The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet"
The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet"
The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet"
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"
The panel encountered a problem while loading "OAFIID:GNOME_WorkspaceSwitcherApplet"
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet"
The panel encountered a problem while loading "OAFIID:GNOME_WindowListApplet"
The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet"

Now I have no wireless network connection. The LAN connection works but Firefox and Thunderbird do not. Generally the desktop is really messed up!

I've tried reinstalling ubuntu-desktop, gnome-applets etc but to no avail.

I've attached the bash_history so you can see what I've done - can anyone help with this?

---

### Post by Habitual on 2010-11-29
Try re-creating the panels. You will lose custom launchers, layout, etc.

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

Logout/in

---

### Post by Jamesss on 2010-11-29
Thanks, didn't work though. I still get the messages popping up on reboot. It might also be worth mentioning that whenever I right-click the panel and click Add to Panel, gnome-panel exits and restarts with the same error messages

---

### Post by Jamesss on 2010-11-29
Also, I can't get synaptic to run:

Segmentation fault

Any ideas? I really need to get my computer back up and running again!!

---

### Post by Habitual on 2010-11-29
Well, pewp.

You *could* mv ~/.config ~/.config.org and ~/.gconf ~/.gconf.org 
(this will effectively re-set ALL your preferences.)

To do this logout of the desktop and open a session with Ctrl+Alt+F1
login as root.
cd /home/**USER**--> ***USER*** is YOUR username/identity.
mv .config .config.org 
mv .gconf .gconf.org
exit the console session.
Ctrl+Alt+F7 and login.
all Gnome Settings reset.

You will of course, have to rebuild Gnome Panel launchers, etc.
**This will NOT affect your Desktop** launchers.
But perhaps someone else has a better way...?

Have you tried to remove these installed programs from c-li?

---

### Post by Jamesss on 2010-11-29
Thanks again for your help. Unfortunately that didn't work either. I've tried removing the two programs and associated libraries I installed earlier and that hasn't helped either.
Firefox, Thunderbird, Rhythmbox, Epiphany, F-Spot, and Sound-Juicer all report:
Segmentation Fault.

Do I really have to do a complete reinstallation?!?

---

### Post by Habitual on 2010-11-30
I'd backup all the stuff you want to keep and consider it.

---

