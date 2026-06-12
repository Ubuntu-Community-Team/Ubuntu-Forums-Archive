---
title: "How do i remove the Netbook interface?"
date: 2010-05-24
forum: General Help
---

### Post by David Deu on 2010-05-24
I'm using the Ubuntu 10.04 Netbook Remix and therefore I have the built-in netbook interface: (pictured)
[ATTACH]158071[/ATTACH]

Is there any way to remove this and get the standard desktop? because in this one I don't really have a desktop and can't create Shortcuts to specific files and folders.

Thanks,
David

---

### Post by Chesamo on 2010-05-24
```
sudo aptitude purge ubuntu-netbook && sudo aptitude install ubuntu-desktop
```
This will uninstall the UNR system and install a standard Ubuntu system.

---

### Post by David Deu on 2010-05-24
I didn't understand, it will remove just the "Netbook desktop" and rather install a standard desktop, or this installs another version of the whole Ubuntu.

---

### Post by geirha on 2010-05-24
Use the desktop switcher to switch to classic mode. Should be in System -> Preferences somewhere.

---

### Post by David Deu on 2010-05-24
> **geirha said:**
> Use the desktop switcher to switch to classic mode. Should be in System -> Preferences somewhere.
Couldn't find.

---

### Post by David Deu on 2010-05-25
Any solution?

---

### Post by dino99 on 2010-05-25
look at settings with gconf-editor

---

### Post by David Deu on 2010-05-25
How do I get to the settings in gconf-editor?

---

### Post by enz1m3 on 2010-05-26
You should open a terminal (Accessories - Terminal) and type "gconf-editor" to open the gconf-editor

But anyway, I'm also having this problem and I can't disable the netbook interface...

---

### Post by kerry_s on 2010-05-26
> **David Deu said:**
> I'm using the Ubuntu 10.04 Netbook Remix and therefore I have the built-in netbook interface: (pictured)
[ATTACH]158071[/ATTACH]

Is there any way to remove this and get the standard desktop? because in this one I don't really have a desktop and can't create Shortcuts to specific files and folders.

Thanks,
David

to create shortcuts drag & drop them on the icon on the left side on the panel, it will then be added to favorites. for files & folders you just have to bookmark them in the file manager.

---

### Post by fooman on 2010-05-26
can't you just choose gnome at the login screen?  should be no need to uninstall/disable anything...the netbook interface will still be an option if you decide to go back and try it again.

choosing gnome at the login screen (click once on your name,  then at the bottom of the page choose gnome from the list), will get you to a normal looking ubuntu desktop.

---

### Post by David Deu on 2010-05-26
> **fooman said:**
> can't you just choose gnome at the login screen?  should be no need to uninstall/disable anything...the netbook interface will still be an option if you decide to go back and try it again.

choosing gnome at the login screen (click once on your name,  then at the bottom of the page choose gnome from the list), will get you to a normal looking ubuntu desktop.
THANK YOU!
It worked!

---

### Post by enz1m3 on 2010-05-26
> **fooman said:**
> can't you just choose gnome at the login screen?  should be no need to uninstall/disable anything...the netbook interface will still be an option if you decide to go back and try it again.

choosing gnome at the login screen (click once on your name,  then at the bottom of the page choose gnome from the list), will get you to a normal looking ubuntu desktop.

Yeah, I just figured that out also, thank you so much :D

---

### Post by chafic2783 on 2010-05-31
Perfect.  Simple solution.  Much obliged for the tip.

Regards,
Chafic

---

