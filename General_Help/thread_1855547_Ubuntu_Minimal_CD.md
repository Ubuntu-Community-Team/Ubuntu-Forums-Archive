---
title: "Ubuntu Minimal CD"
date: 2011-10-06
forum: General Help
---

### Post by erbad on 2011-10-06
Let me start by saying that I am a complete newbie to Linux and Linux commands.

I've been reading about the Ubuntu Minimal CD and would like to really trim the fat from my installation.

All I really need is:

Ubuntu minimal install
Google Chrome
Text editor
screen lock
Access to synaptic package manger
Gnome desktop (I believe this is the one used on the Ubuntu desktop)

Would someone know where I could find a list of commands on how I would install each of these services after installation of the minimal CD?

Thank you

---

### Post by nothingspecial on 2011-10-06
You need a wired connection.

```
sudo apt-get update && sudo apt-get install x11-xserver-utils gnome-core gedit chromium-browser
```

That ought to do it although  I may have forgotten something.

---

### Post by erbad on 2011-10-06
> **nothingspecial said:**
> You need a wired connection.

```
sudo apt-get install x11-xserver-utils gnome-core gedit chromium-browser
```

That ought to do it although  I may have forgotten something.

Thank you for the instructions.

Just to confirm, if I go this route, my installation will not have OpenOffice, Firefox and the other apps that get installed with a default installation.

---

### Post by nothingspecial on 2011-10-06
No, but bare in mind, I edited my instructions to include updating which I forgot.

Also gnome-core itself comes with it's own epiphany browser, totem, evince, brasero and a whole bunch of other stuff.

If you want to go truly minimal consider something like openbox.

---

### Post by erbad on 2011-10-06
> **nothingspecial said:**
> No, but bare in mind, I edited my instructions to include updating which I forgot.

Also gnome-core itself comes with it's own epiphany browser, totem, evince, brasero and a whole bunch of other stuff.

If you want to go truly minimal consider something like openbox.

I'm comfortable with gnome, so I'm going to stick with this, but perhaps I'll load up another minimal install with openbox in a VM just so I can see what is the difference.

Thanks again for the instructions, I'll give this a try today.

---

### Post by jerrrys on 2011-10-06
[gnome desktop packages]("http://packages.ubuntu.com/natty/gnome-desktop-environment")

---

