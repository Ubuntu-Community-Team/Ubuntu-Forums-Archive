---
title: "Accessing installed Apps via Synaptic"
date: 2009-07-12
forum: General Help
---

### Post by ump001 on 2009-07-12
I've installed a few apps via Synaptic, but i can't see them anywhere in my app menus. They have definitley installed as i've tried uninstalling a reinstalling via Synaptic.

When checking tha app properties they seem to be under a Misc section which i cannot find?

---

### Post by lordofallhearts on 2009-07-12
What you can do is go to System > Preferences > Main Menu
You can now see all installed apps including those which arent shown.You can modify your menu as you like.

If your problem persists , reply with the app name and details.

---

### Post by ump001 on 2009-07-12
hi,

Have tried the Main Menu, but can't see the apps there either.

I've installed: Eterm, vmware-server.

---

### Post by whole.grains on 2009-07-12
Weird, I installed Eterm and it did the same thing to me. I could launch it from the terminal, but I didn't see it in any menu. You can add it yourself from System>Preferences>Main Menu> +New Item

---

### Post by ump001 on 2009-07-12
Yes was going to do that, but am a little new to ubunut, so unsure of where to find all the apps. Any ideas? Have tried searching but only seem to find the manuals...

---

### Post by whole.grains on 2009-07-12
I'm not sure. Other things I install from Synaptic show up in the menus.

---

### Post by ump001 on 2009-07-12
Thanks for your help whole.grain.

Anyone else got any idea?

---

### Post by Piccy on 2009-07-12
Go to System - Preferences - Main Menu
Click new item

From here its just a matter of creating a new launcher

I assume its an app so select 
Type: application
Name: Call it what you want
Command: Put the name of the package in here (same as what its called in synaptic). In this case just type eterm, or 
click browse. It would probably be installed into the /usr/bin directory

If you want to make it pretty, click the springy icon and select a picture you want as the icon

---

### Post by ump001 on 2009-07-12
ok, this hasnt worked either. I try and add a new item, type eterm (same as synaptic) this doesn't seem to exist. Also can't see any of the apps in /usr/bin?

Just installed virtualbox, which shows up in the menu fine?

---

### Post by whole.grains on 2009-07-12
Don't forget to capitalize the E in Eterm in the box that says 'command'.

---

### Post by ump001 on 2009-07-12
thanks, that seems to work fine for Eterm. But not for some other packages i've tried....

Appreciate your help.

---

### Post by oldos2er on 2009-07-12
If no menu entry is created, try running the program in a terminal or with Alt-F2. You can use either Synaptic or dpkg to see where each file in a package has been installed; in Synaptic, right-click on an installed package, choose Properties, Installed Files. Or run dpkg -L [package name].

---

