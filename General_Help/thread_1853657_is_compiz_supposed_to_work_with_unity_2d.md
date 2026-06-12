---
title: "is compiz supposed to work with unity 2d?"
date: 2011-10-02
forum: General Help
---

### Post by mozozo4 on 2011-10-02
HI, i am new to ubuntu and need some help.
I had to switch from ubuntu 3d to 2d because my computer was lagging too much. Does compiz work with unity 2d because i have tried to activate an animation but i don't see it working.

Can someone please help me?

---

### Post by Krytarik on 2011-10-02
By default, Metacity is run in the Unity 2D session, but you can change its session settings to run Compiz instead.

Therefore, open "/usr/share/gnome-session/sessions/2d-ubuntu.session":
```
gksudo gedit /usr/share/gnome-session/sessions/2d-ubuntu.session
```
Change this:
```
[GNOME Session]
Name=Unity 2D
Required=windowmanager;panel;filemanager;
Required-windowmanager=[COLOR=Red]**metacity**[/COLOR]
Required-panel=unity-2d-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;unity-2d-launcher;
FallbackSession=classic-gnome
```To this:
```
[GNOME Session]
Name=Unity 2D
Required=windowmanager;panel;filemanager;
Required-windowmanager=[COLOR=Red]**compiz**[/COLOR]
Required-panel=unity-2d-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;unity-2d-launcher;
FallbackSession=classic-gnome
```
Save the file, and relogin.

Greetings.

---

### Post by mozozo4 on 2011-10-02
it worked !!!!!!!!!!!

thank you so much Krytarik

---

