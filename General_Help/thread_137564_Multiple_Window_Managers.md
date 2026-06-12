---
title: "Multiple Window Managers"
date: 2006-02-28
forum: General Help
---

### Post by Prospero2006 on 2006-02-28
I'm thinking it's time I set my system up so I can choose window managers at login. Right now, I run KDE. If I install the 'gnome-desktop' packager, what's going to happen. Does anyone have multiple window manager selection set up?

Thanks,
Pros

---

### Post by schmappel on 2006-02-28
Yep, I do! Just can't seem to decide over which one to use :)
If you install the 'gnome-desktop' you get to choose a session at login. If you don't specifically choose one at the KDM screen it boots into your default choice. Piece of cake!

---

### Post by Jucato on 2006-02-28
This I would also like to know. I have, in the past, installed the enlightenment window manager (e16). It was a worked fine, but I'm not sure if I did everything correctly. I just installed everything through synaptic/adept. I wish there was a guide on how to change window managers for KDE. The HOWTO's only have something for GNOME.

Btw, gnome-desktop (is there a package with this name?) is going to install the GNOME desktop environment (something like install ubuntu-desktop), not a window manager.

---

### Post by tadashi on 2006-02-28
Yep, it is actually really easy. When I tried Ubuntu I just used the package manager and loaded up the KDE core (and maybe base but not sure) files and the apps I wanted.  Do not install the KDE desptop unless you want all the KDE applications.

Now that I did a Kubuntu fresh install I installed gnome windows manager and a few apps using the package manager.  Now I can just select which session at login.

---

### Post by Mau on 2006-02-28
Is the install process easy?  For example, just do an apt-get, reboot, and I could login to GNOME or Enlightenment?

---

### Post by tadashi on 2006-02-28
I found it easier using the package manager since I did not know the names of the packages to do the apt-get.  The package manager I was able to select the desktop and any applications I wanted.  Hit the committ button and reboot when it was done.

---

### Post by Jucato on 2006-02-28
Yeah, the package manager is a bit better, just be careful in using adept, since the only prompt that you get about stuff that will be installed, removed, or upgraded is found in an inconspicuous status bar. 

OT: Just wanted to clarify. I'm not sure what Prospero really wanted to install, but GNOME is not a window manager. It is a desktop environment similar to KDE and Xfce. It is a system that integrates the operating system and it's applications. Window Managers are responsible for how the windows look, nothing more. Desktop Environments are sort of like engineers that make sure everything work together properly, while Window Managers are interior designers that make stuff look good. :D

That being said, when you install the GNOME desktop over KDE, it will install some other GNOME applications with it. And it might be good if you try to take note of what stuff will be installed/removed, so that you can also uninstall it easily. For this I use the following technique:
1. In Adept/Synaptic, try to find the package names of what you want to install and try to see what will be installed with it.
2. In the terminal, use apt-get so that you will have a list of packages to be installed. Copy these and paste it to a document for future use. That way, you can just open this document, copy the contents and apt-get remove it easily in one swoop. :D

---

