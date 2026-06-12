---
title: "Would there be any problem if I shared the same home partition?"
date: 2011-10-15
forum: General Help
---

### Post by blah... on 2011-10-15
I already have Ubuntu 11.10 installed with its separate root and home partition. I have 20 GB of free space, could I install Xubuntu on that and have it use the same home partition with no problem?

---

### Post by mcduck on 2011-10-15
Yes you could, assuming you are happy with using the same settings for all your programs on both Ubuntu installs.

On the other hand there's not much of a reason to do such thing, you could just as well install XFCE on your existing Ubuntu install and switch between the two desktops from the login screen, saving you from the extra work of managing two separate operating systems, booting to switch between them, and of course from wasting loads of disc space. :)

---

### Post by vanadium on 2011-10-15
I agree, since both are the same Ubuntu versions, with the same versions of the application software. Thus, there is no chance of having config files that are only compatible to one of the instals.

The advantage of having both desktops as separate installs is that there will be strict separation and no clutter: in the menu's, you will only have the software you want in that desktop. Starting Ubuntu, you will have the Ubuntu greeter. Starting Xubuntu, it will be the Xubuntu one. The drawback is that you need to reboot in order to switch.

---

### Post by mcduck on 2011-10-15
It's possible to configure applications to only show in a certain desktop environment's menus.

The .desktop files used for launchers and menu entries have *OnlyShowIn* and *NotShowIn* options which can be used to define which programs show where. I remember even seeing automatic scripts for hiding KDE apps in Gnome and vice versa, I'm pretty sure there must be one for XFCE as well if you don't feel like doing it by hand.

With only 20GB of extra space available I'd definitely go that way instead of having a duplicate of every single system and program file taking the space. Not to mention having to update all those files twice... Better leave the last gigabytes to personal files instead... :)

---

### Post by vanadium on 2011-10-15
> **mcduck said:**
> 
With only 20GB of extra space available I'd definitely go that way instead of having a duplicate of every single system and program file taking the space. Not to mention having to update all those files twice... Better leave the last gigabytes to personal files instead... :)
I also would rather work with a single installation.

---

### Post by mcduck on 2011-10-15
I tried to look for an automatic way to edit the application launchers to hide XFCE apps in Gnome and Gnome apps in XFCE, but since XFCE app launchers are stored in the same location as Gnome apps are (unlike KDE which stores them in it's own subdirectory) there doesn't seem to be any nice way to do that.

You can still edit the .desktop files by hand. It's really easy, but will probably take a while to do if there are many programs you wish to only show in a certain desktop environment.

---

