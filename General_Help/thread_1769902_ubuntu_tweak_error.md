---
title: "ubuntu tweak error"
date: 2011-05-28
forum: General Help
---

### Post by soylentcola on 2011-05-28
So I'm trying to run the update manager through Ubuntu Tweak, and every time I try to install updates, I get the error: "Could not apply changes! Fix broken packages first."

I've gone into my terminal and run sudo apt-get update with no problems, so I'm not exactly sure what packages are causing the issue, can someone help me out?

---

### Post by linuxinstalledfromhdd on 2011-05-28
Did you install it from the PPA like this:

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

---

### Post by soylentcola on 2011-05-28
> **linuxinstalledfromhdd said:**
> Did you install it from the PPA like this:

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

I just ran that (I had originally installed Ubuntu tweak through a script file) but I have Ubuntu Tweak at the latest version apparently, so it did me no good. :(

---

### Post by linuxinstalledfromhdd on 2011-05-28
Uninstall the script. Back trace your steps.  And then use the PPA above to install it.

If you can't fix it yourself, then here is a walk-through to get things working again on your system.

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by fragos on 2011-05-28
Run Synaptic Package Manager, Edit menu and select "Fix Broken Packages". That should clear it up.

---

