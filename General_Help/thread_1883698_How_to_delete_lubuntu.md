---
title: "How to delete lubuntu"
date: 2011-11-19
forum: General Help
---

### Post by esg10 on 2011-11-19
How do I Completely Remove/Uninstall LUBUNTU via Terminal?
any help will be kindly appreciated.

---

### Post by JC Cheloven on 2011-11-19
How did you install it and what had you installed previously?
For instance, did you have a regular Ubuntu installation and ran the command ```
sudo apt-get install lubuntu-desktop
``` or some equivalent action?

---

### Post by esg10 on 2011-11-19
I was already on 11.10 Oneiric Ocelot.

I got Lubuntu through the terminal just like you typed it.

Got any idea how I can get rid of it?

---

### Post by JC Cheloven on 2011-11-19
Ok. For your records, lubuntu-desktop is what is called a "meta package", a kind of pointer to other packages to be installed. Removing the meta package will not remove that "other packages". So don't bother to try that. 

A lot of packages are installed with lubuntu-desktop. A way of getting rid of them (it's that comes to my mind right now anyway) is to look at the history in synaptic, see what was installed at that time, and removing it manually from synaptic itself. I don't use software center much, I'm not sure it it offers a better option. Also I'm not sure what would happen with the login manager.

SO BETTER CONSIDER THIS:

At the time of login you can choose (from the menus at the bottom of the screen) the desktop environment you want to boot to. Simply choose another desktop (ubuntu, unity2D or whatever your choice is). Your choice will be remembered for future boots. And if you don't like to see so many apps in your menus, remove manually some of the ones you don't like (for example lubuntu has installed abiword, gnumeric,chromium browser, osmo, galculator, leafpad, and some others that you may want to remove). This would be my advice.

---

### Post by JC Cheloven on 2011-11-19
Oh, and after removing things, you can run ```
sudo apt-get autoremove
``` to clean up dependencies no loger used.

---

### Post by Gremlinzzz on 2011-11-19
> **esg10 said:**
> How do I Completely Remove/Uninstall LUBUNTU via Terminal?
any help will be kindly appreciated.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
:popcorn:
follow instructions

---

