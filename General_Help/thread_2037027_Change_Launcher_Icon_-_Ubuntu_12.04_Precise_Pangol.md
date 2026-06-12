---
title: "Change Launcher Icon - Ubuntu 12.04 Precise Pangolin"
date: 2012-08-03
forum: General Help
---

### Post by Hedgehog9597 on 2012-08-03
I want to change the icon for an application, specifically IDLE (using Python-3.2).  I would like to know where the icons for applications are stored, as I imagine all I need to do is replace the file.  Thanks!

---

### Post by itagomo on 2012-08-03
icons are in:
possible locations:

[B]/usr/share/icons/
[/B]/usr/share/app-install/
/usr/share/app-install/icons/
/usr/share/pixmaps

---

### Post by MG&amp;TL on 2012-08-03
You'll want to look in /usr/share/icons/ . If your current icon theme doesn't have an icon for IDLE, it will fall back to the icon in the hicolor/ directory.

Alternatively, install the 'main menu' app and edit it from there.

---

### Post by Hedgehog9597 on 2012-08-03
After I installed idle, the icon is just a blank square with a question mark in the middle.  So I assume  So, where in hicolor/ should I put the now icon? And how do I know what to name it?

I guess I am not really changing launcher icon, since there was never one to begin with... I am just creating one.

---

### Post by MG&amp;TL on 2012-08-03
You can put a new icon in /usr/share/icons/hicolor/apps/<size>/idle.png and edit IDLE's .desktop file in /usr/share/applications/idle.desktop (or similiar) to *add* the line:

```
Icon=idle
```where <size> is the size of your icon (resize the icon to fit one of the existing folders), or you could make it much simpler and install the *main menu* (alacarte) app, which has some buttons to do this for you.

And no, I don't know why the IDLE developers can't do this themselves.

---

### Post by Hedgehog9597 on 2012-08-03
I used main menu to change the icon, and here is what happened.

First: exactly what I did:

1. I moved the new icon, dimensions 256x256, to /usr/share/pixmaps
2. I opened main menu, navigated to IDLE, clicked on the icon, and selected the new icon.

What happened:
That icon DOES have a new icon, namely, when I search 'IDLE' in the dash, and it pops up, it has the new icon.

However, when I run the application, the application still has a question mark icon on the Launcher.

What is wrong?  And I did log out and back in, just to make sure settings had been applied and whatnot.

Edit: I also checked, and the size of the icon isn't the issue, as Thunderbird mail displays it's icon perfectly, and it uses a 256x256 icon as well (I checked in main menu).  Also Firefox uses a 128x128, so I don't think size matters here.

---

### Post by MG&amp;TL on 2012-08-04
I could be wrong here, but I think what the icon displays in the launcher is application-defined, as opposed to what it displays in the Dash. So if you want an icon for that, you might need to contact the devs.

What happens if you pin it to the launcher?

---

### Post by Hedgehog9597 on 2012-08-04
> **MG&TL said:**
> What happens if you pin it to the launcher?

Interesting... when I pin it to the launcher, it has its icon! Yay!   But... I have found out that all it is is a .desktop file.  So... when I   click on it, it then opens idle (which is a .pyw file) and a NEW ICON   pops up on the launcher, titled "*python shell*" and with the question   mark icon.  Is it even possible to give this particular thing an icon?   I  could find the question mark icon and replace it, I guess, but that   would be a workaround.

Edit: Workaround worked!  I found the question mark icon files, in /usr/share/icons/Humanities/apps/<various sizes>/application-default-icon.svg, renamed the files to application-default-icon_old, then put a python svg in those folders with the name application-default-icon.svg.  It worked!  Just from now on, whenever ANY program without an icon is opened, it appears on the launcher with a python icon... hopefully I won't run into any no-icon programs besides idle.  Yay, workaround!

---

### Post by Hedgehog9597 on 2012-08-04
Sorry, double post.

---

