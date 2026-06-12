---
title: "Can't convert standard 9.10 Desktop into Netbook Remix"
date: 2010-02-17
forum: General Help
---

### Post by cyclone5uk on 2010-02-17
I have been trying to convert my standard 9.10 desktop installation into the Netbook Remix version.

I assumed that all I had to do was add “Netbook Remix Launcher” from synaptic and set it run at startup.

However, it doesn’t work and I’m left with a normal desktop view after rebooting.

According to the Wiki these are the packages that constitute the UNR:

Desktop Switcher - Allows the user to switch between two desktop modes. Currently supports switching between Ubuntu Netbook Remix mode and "Classic Ubuntu" (two panels, gnome-like) mode. 

Go Home Applet - A gnome-panel applet that, when clicked upon, displays the desktop. Used in a netbook-based desktop, the desktop-window will normally be the launcher. Go Home Applet also works in conjunction with the netbook-remix-launcher whereby dragging and dropping a file/url/application to the go-home-applet will automatically add it to the launcher's favorites section. 

Human Netbook Theme - A gtk theme for use with Ubuntu Netbook Remix 

Maximus - A desktop daemon which will automatically maximise and, optionally, un-decorate windows. Has support for exclusion lists and will work with any EWMH-spec compliant window-manager. 

Ubuntu Netbook Remix Launcher - An easy-to-use 
program/places/favourites launcher which resides on the desktop, replacing the main-menu. 

Window Picker Applet - A gnome-panel applet that displays open windows as icons on the panel, and has integrated window title-bar functionality. Optimised for use on netbook-size screens. 

None of them seem like dependencies for the Ubuntu Netbook Remix Launcher itself, so I cant understand why it isn’t working. I’ve turned of compiz and disabled AWN.

---

### Post by ajgreeny on 2010-02-17
I tried this a while ago, but hated it so quickly removed it, but nevertheless, I seem to remember that it was just available as another session in the login window, in the same way you can choose kde or gnome.  What annoyed me most was that it completely changed all my settings in ~/.gconf so when I removed UNR from the system, I had to completely reset all my configuration back to what I normally use, which is very different to the default.

The moral of this story: keep a backup of ~/.gconf so you can get back to what you had before you tried UNR

---

### Post by cyclone5uk on 2010-02-18
Fixed it now - Turns out I was missing a package: "Default settings for UNR" which contains the Gconf defaults for UNR.

---

