---
title: "Ubuntu with KDE-desktop. Choose between Gnome and KDe in grub"
date: 2009-10-20
forum: General Help
---

### Post by madsc89 on 2009-10-20
I am currently sitting on Ubuntu Karmic.
However, I would like to explore KDE, therefore I installed Kubuntu-desktop (and dependent packages) on top of my existing Gnome install.
So far so good, it works, I am able to choose between the two at log in, etc.
However, the whole system (besides the actual GUI) now seems to be a mixed "mess" between Kubuntu and Ubutnu. On startup, both Kubuntu and Ubuntu loads (taking a lot more time than earlier), on shutdown, only Kubuntu flash appears, in KDE, a LOT of my RAM is used, and so on.

My problem is that I would like to separate KDE and Gnome more. So that the system loads and run KDE -or- Gnome, not a mix. Choosing between the two in Grub menu would be perfect (perhaps by spescyfying some commands to the entries in the grub menu?), as I dualboot anyways. It have to be the same foundation install, though, because I dont want to maintain files, programs on two different OS.

How do I best proceed to better separate KDE and Gnome. My current solution takes a lot of resources and makes the computer slow at startup. Also I prefer to skip the login screen, which makes me having to log out just after startup in order to choose a differnt environment than the one I earlier shut down with.

Thank you.

---

### Post by flipper9 on 2009-10-22
I have the same question. On prior attempts to do this, it always "seemed" to screw up my system with wierd things going on when using KDE or Gnome.  On the last attempt, I just resorted to reinstalling Ubuntu as I didn't want to figure out how to fix it.  Anyone have experience running both?

---

### Post by ranch hand on 2009-10-22
The best way to do that, and give each "flavor" all its glory, isto install an three partitions.

A / for Ubuntu, a / for Kubuntu, and a common /home.  Make sure you use different user names for the two "flavors".

---

### Post by Falc7 on 2009-10-22
> **madsc89 said:**
> I am currently sitting on Ubuntu Karmic.
On startup, both Kubuntu and Ubuntu loads (taking a lot more time than earlier

What do you mean they both load?

---

### Post by sakisds on 2009-11-18
Try installing kubuntu-desktop with the following command:
 
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```
 
This will install a full kde desktop but without a lot of kde applications like music players, cd burners, instant messengers...
 
I used it before and it worked fine.
(This will mess up a bit the system and the settings section, you can fix it through with the menu editor of kde and gnome)

---

### Post by madsc89 on 2009-11-19
Thank you.

Whith both ubuntu and kubuntu loading I mean that both their loading skreens appears before login sreen. The kubuntu logo with progress bar shows, then white ubuntu logo, then ubuntu splash. (or somethig like that.)

---

