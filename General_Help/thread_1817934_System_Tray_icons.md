---
title: "System Tray icons"
date: 2011-08-04
forum: General Help
---

### Post by unknown user on 2011-08-04
I have a few applications open and running (in the background), such as firestarter firewall and mail notification. These are good, but the icons for them are placed in the side bar, which appears when the mouse is over the left hand side of the screen and disappears when the mouse is moved away. Sorry not know the name for it. This is good, but as they are not used like the office writer and firefox are, so it would be nice to have them in the system tray/bar at the top of the screen where the clock, calendar and network connections icon is. Does anyone know how I can move the icons to this tray/bar?

---

### Post by isackja on 2011-08-04
try this link.
[http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-add-the-classic-gnome-menu-applicationssystemwine-to-the-unity-panel-system-tray/](http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-add-the-classic-gnome-menu-applicationssystemwine-to-the-unity-panel-system-tray/)
then try dragging a shortcut/launcher to the bar.

---

### Post by EkuquoL on 2011-08-04
If you turn off certain applications in the task manager you could break the functionality of some programs. 
Xorg and gnome have orbiter and other small background apps that run constantly and *need* to run/Sleep* constantly.
Sleeping means it is just idle .

Xorg is the system controller of the Window framing system
Gnome is the engine of the Unity interface/ GUI
 
You can go to both gnome.org or x.org to learn more about them. 
You can even type in the Terminal
 man Xorg 
 man gnome

for the manual and brief summary of the Xorg/gnome engines.
man is the Manual command ... For reading the manual. Press Q anytime you want to exit the manual.

If you want to uninstall unneeded software just use the package-manager and uninstall it that way.
Just keep-in-mind that you read the entire *Dependency List* ... Because -- As I already Said -- Gnome and Xorg have quite a few dependencies that are needed to remain Secure and stable.

---

