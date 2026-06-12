---
title: "Gnome ok, KDE not"
date: 2009-11-02
forum: General Help
---

### Post by utnubuuser on 2009-11-02
Hello  --- anyone able to describe the main differences in the way the two environments deal with xorg?  (KDE/Gnome)

I'm mostly a Ubuntu user, but from time to time I like to try Kubuntu because KDE is such a fantastically integrated system.

I've never been able to get a decent install of Kubuntu on my particular hardware,

I decided to try the Kubuntu version of 9.10, and as per usual, no go.

I can use the live CD ok, and I can install, but when I boot from the new hdd install, my xorg is messed.

My gear isn't unusual.  A normal Ubuntu install doesn't require any configuring to function.  -- good to go right out of the box.

So on my new Kubuntu install, everything is working, except my panels and the title-bars of apps.  

So I open a terminal, type apt-get install Ubuntu-desktop, wait for it to download and install, then reboot.  Bingo.  Works like charm.  

PLUS: now my Kubuntu desktop works too!

Anyone got any idea why this might be the case?

The only difference is that with the Ubuntu-gnome installed, I can use gdm as the default rather than kdm.  Would that be it?


Thanks.

---

### Post by jbrown96 on 2009-11-02
I'm not totally sure what you mean. Could you attach a screenshot (press PrintScreen and a dialog will appear)?

---

### Post by utnubuuser on 2009-11-02
No, not anymore since I installed the Ubuntu-desktop.  Basically,  The bottom panel, where the clock and the buttons for the application etc are usually to be found is there, except the rendering is messed up.  All I get is a bunch of garbled graphics that are unrecognizable.  Because I know where to click to bring up the "favorites" popup, and because I can then click on the areas where the Browser, the File-manager etc are supposed to be listed, I know they work, they just won't render (in the menus).  - Once the applications are launched, they function ok, ie I can see the menus in Dolphin and Konqueror, and I can access websites,  but the area of the desktop where they're supposed to be launched from is messed.
As I've said,  as soon as the ubuntu-desktop is installed, everything in the Kubuntu-desktop renders ok too.
There must be some basic default configuration file that's getting the right signal from the gnome environment, but not the kde environment.

The hardware has an older ATI card that uses the open-source driver, but again, gnome recognizes everything ok, but not kde. - except with Ubuntu-desktopinstalled, in which case the KDE rendering fixes itself.

Are GDM and KDM involved in the configuration on a level deeper than the login?

One of the other symptoms of the Kubuntu desktop is that it won't let me log in either.
ie, I input my user and my password, the screen refreshes, then lands back at login as though I'd put in the wrong password,(which is not the case), - again, as soon as I add the Ubuntu environment to the Kubuntu install,  login works, - mind you, that's by using GDM instead of KDM, which is why I'm asking about kdm/gdm.

---

### Post by utnubuuser on 2009-11-02
Whatever the issue is/was, it's fixed now.

I reinstalled kdm and that component is now working as it should.

There must have been a slight corruption of kmd somewhere the either gdm, or the reinstallation of kdm has fixed.

Kudos to the Kubuntu/KDE devs, for an absolutely beautiful desktop.

---

