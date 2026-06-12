---
title: "Kubuntu crashes regularly"
date: 2006-02-08
forum: General Help
---

### Post by WujekSamoZlo on 2006-02-08
I'm new to Linux and Kubuntu altogether. I like it very much and I think I'll stick to it for quite a while. Everything works fine, but I have this one annoying problem - sometimes, the system just sends me to the konsole login (text mode, not the Konsole wrapper), then immediately to the KDE login window. I login and it works fine. It happens regularly, about 3, 4 times a day, but I don't know the causes. Sometimes when I browse the WWW pages, sometimes when I fiddle with amaroK or aMule. I don't have to say it's a rather unpleasant behaviour. I am not doing anything important these days, so it's not a big deal. But when I get used to the new OS (and this moment  is soon) I am going to do some programming and other stuff, and it will be unacceptable.
Has anobody experienced such a problem? And what you did to get rid of it?
Thanks.

---

### Post by MartinG on 2006-02-08
This is your X-server crashing.  What video card do you have, and what driver are you using?

In the meantime, when you're at the login screen choose a console login and run "sudo dpkg-reconfigure xserver-xorg", and check the choices you make (the original install does this automatically, and sometimes makes bad choices).

---

### Post by WujekSamoZlo on 2006-02-08
I have an ATI Radeon 9550, and I installed a driver myself, after a few tries (I downloaded it from the ATI homepage). Finally what I got is an ATI icon in the K-menu, which says it's a version 8.21.07.
I did it because the Fireworks 3D screen saver would run slow. After my installation it runs very well, and so does the Tux Racer game.
What do you suggest?

---

### Post by MartinG on 2006-02-08
As I feared, an ATI card.  I use NVidia, and so am sketchy on ATI, but I *believe* they are a bit error-prone.  Can I suggest that you review and if necessary repeat your installation, using the instructions in this HOWTO:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

If that doesn't do the trick there is a (long) discussion thread to work through.

---

### Post by WujekSamoZlo on 2006-02-08
Thank you very much, I'll read it all if necessary.

But I have a question: I'm going to make a clean install of kubuntu, and, unaless it's necessary, I'm not going to install any ATI drivers, just stick to those that are in the distro. Can I do that? I mean, 3D games and screensavers aren't my priority, but I would like to watch fullscreen films. Is it a good option?

---

### Post by MartinG on 2006-02-09
As far as I know, there should be no problem for what you want.  There are in fact two drivers available from Ubuntu, the one included in the basic installation and one from one of the extra repositories (the "restricted" one, I think).  This second one should be trouble-free, as it is supported by Ubuntu, so **if** you're not happy with the basic one, try it.

To do this, after your basic installation enable the extra repositories in Adept Manager by going to Adept->Manage Repositories and looking for all the greyed out lines that include "deb" or "deb-src" under "type". Right-click on them, choose "enable", and press "Apply".  Exit the Repository Manager and fetch updates. now search for xorg-driver-fglrx, and install it.

All the best.

---

### Post by Mustard on 2006-02-09
I'd just mention that gnome used to randomly crash to the login prompt for me when my RAM stick started failing.  In my logs it showed up as a fatal x error.  I ran memtest from the grub boot menu, which confirmed my RAM was faulty and then bought two new RAM sticks and everything is working fine now.

---

