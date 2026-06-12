---
title: "Items Removed From Menu"
date: 2009-10-17
forum: General Help
---

### Post by Jason Cook on 2009-10-17
In the menu I am missing most the system menus. In the System>Preferences category I only have File Management & Multimedia Systems Selector. Is their any way to add the other items back?

---

### Post by Sam on 2009-10-17
Right click on the menu applet, choose "Edit Menus". Go into "Preferences" on the left and check whatever you need on the right.

---

### Post by Jason Cook on 2009-10-17
> **Sam said:**
> Right click on the menu applet, choose "Edit Menus". Go into "Preferences" on the left and check whatever you need on the right.
I do that and in Desktop>Preferences I still only see File Management & Multimedia Systems Selector which are the only items that are currently visible.

---

### Post by Jason Cook on 2009-10-26
bump

---

### Post by cwbar_1 on 2009-10-26
Do you have "terminal?"
If so, navigate to /name_of_your_home_folder/.config/menus  . See if you have the 2 files applications.menu and settings.menu  .   Are these 2 files there?  If so,  copy and post the contents of these 2 files.  I'll see what I can do.

I've also read in several forums that deleting these 2 files and restarting the system will restore the correct menus.

---

### Post by Jason Cook on 2009-10-27
> **cwbar_1 said:**
> Do you have "terminal?"
If so, navigate to /name_of_your_home_folder/.config/menus  . See if you have the 2 files applications.menu and settings.menu  .   Are these 2 files there?  If so,  copy and post the contents of these 2 files.  I'll see what I can do.

I've also read in several forums that deleting these 2 files and restarting the system will restore the correct menus.

I am at school right now. I will try this later. I do still have the terminal. [I don't have nautilus and I am trying to get that solved.]("http://ubuntuforums.org/showthread.php?t=1294107") I do have other file viewers installed though.

---

### Post by Jason Cook on 2009-10-27
I have deleted the files and it restored my application menu items (that I wanted removed). It removed some of my System menus which is what I am trying to restore.

---

### Post by facejaso on 2009-10-29
> **cwbar_1 said:**
> Do you have "terminal?"
If so, navigate to /name_of_your_home_folder/.config/menus  . See if you have the 2 files applications.menu and settings.menu  .   Are these 2 files there?  If so,  copy and post the contents of these 2 files.  I'll see what I can do.

I've also read in several forums that deleting these 2 files and restarting the system will restore the correct menus.


I would just like to say thank you, this helped me out as well. Being new to Ubuntu is kind of hard after being a Windows/DOS user for the last 23 years of my life, and these forums are great to help out.

---

