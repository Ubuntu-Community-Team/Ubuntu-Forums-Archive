---
title: "Cairo Dock crashed my Ubuntu"
date: 2010-06-25
forum: General Help
---

### Post by Vigneshwaran on 2010-06-25
I installed Cairo dock and it was working fine until I changed some themes. It crashed my desktop. When I try to login to Gnome or failsafe gnome session, it returns back to the login screen.

Now I logged into xterm and opened google-chrome to type this.

I have uninstalled cairo dock through sudo apt-get remove cairo-dock

But still I can't login. Is there any way to repair my ubuntu or just gnome (through the command line from xterm)? Please help..

---

### Post by bobcollard on 2010-06-25
> **Vigneshwaran said:**
> I installed Cairo dock and it was working fine until I changed some themes. It crashed my desktop. When I try to login to Gnome or failsafe gnome session, it returns back to the login screen.

Now I logged into xterm and opened google-chrome to type this.

I have uninstalled cairo dock through sudo apt-get remove cairo-dock

But still I can't login. Is there any way to repair my ubuntu or just gnome (through the command line from xterm)? Please help..
I doubt that Cairo-Dock is the cause of your problem.  Possibly a recent upgrade caused this.  If you have a backup of your Home the simple fix would be reinstall Ubuntu.

---

### Post by Vigneshwaran on 2010-06-25
I don't want to reinstall ubuntu.. I have installed too many apps.. Is it possible to uninstall and reinstall Gnome? Or Installing KDE on ubuntu will help?

Edit:
I have found the solution.. I did a mistake by simply uninstalling cairo-dock. I have now uninstalled the other packages like cairo-dock-plug-ins, cairo-dock-plug-ins-integration(i think this is the culprit), cairo-dock-data, cairo-dock-plug-ins-data and some other i don't remember

Now I can login very well :)

---

### Post by bobcollard on 2010-06-25
> **Vigneshwaran said:**
> I don't want to reinstall ubuntu.. I have installed too many apps.. Is it possible to uninstall and reinstall Gnome? Or Installing KDE on ubuntu will help?

Edit:
I have found the solution.. I did a mistake by simply uninstalling cairo-dock. I have now uninstalled the other packages like cairo-dock-plug-ins, cairo-dock-plug-ins-integration(i think this is the culprit), cairo-dock-data, cairo-dock-plug-ins-data and some other i don't remember

Now I can login very well :)
Yes, in Synaptic Package Manager find kubuntu-desktop or gnome-desktop and either install or reinstall it.

---

### Post by fabounet on 2010-06-26
probably a driver issue
try using the dock with "cairo-dock -c" until someone fixes the drivers (the ATI are particularily unstable in Lucid)

---

### Post by Vigneshwaran on 2010-06-26
It is solved.. Thank you..

---

