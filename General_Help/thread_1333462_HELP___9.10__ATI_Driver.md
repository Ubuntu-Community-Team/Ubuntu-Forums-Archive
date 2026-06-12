---
title: "HELP   9.10  ATI Driver"
date: 2009-11-21
forum: General Help
---

### Post by Quarkrad on 2009-11-21
Just put 9.10 on a friends PCs (but??) he has a Radeon 9600 ATI graphics card. Basically I have got in a mess - too may web pages; X11, xorg, etc, etc.  I found in the reps EnvyNG that appears to install/uninstall ATI 'things' so I downloaded it.  It is in Apps/System Tools but when I click on it nothing.  Terminal also does not recognise it.  Can anybody help me purge 'everything ATI' and how to install 'what ever I need' on U9.10.

---

### Post by gradinaruvasile on 2009-11-21
You need nothing for that card. The card is old and is not supported by the proprietary drivers. The Ubuntu included drivers SHOULD (i never tried it, only on 9.04 where the drivers were ok) do fine - some games will not work though.

Just move the config file in your home directory if u messed with it:
In a terminal :

sudo mv /etc/X11/xorg.conf $HOME

Other than that, if u installed ati drivers, uninstall them. Just open synaptic ("sudo synaptic" in a terminal) search for fglrx and uninstall everything that is installed and has fglrx in its name. Then reboot.

---

### Post by Quarkrad on 2009-11-21
That is disappointing - but thanks.  I could not get cairo dock working properly.

---

### Post by gradinaruvasile on 2009-11-21
If it has black rectangles, the thing is that you have to use compiz. 
install fusion-icon:

in a terminal:
sudo apt-get install fusion-icon

launch it:
press alt+f2, type fusion-icon, press enter

Right-click on the icon, select compiz.

Then launch cairo-dock (i alwayss use "cairo-dock -c" disabling the opengl backend that eats hell of a lot of memory, but i have fewer effects).

Hope it works...

---

