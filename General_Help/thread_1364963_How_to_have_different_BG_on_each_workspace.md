---
title: "How to have different BG on each workspace"
date: 2009-12-26
forum: General Help
---

### Post by bonfido on 2009-12-26
Hello everyone
I'm new to Linux and i just love it.


How can i set different wallpaper on each of my 4 workspaces.
I believe as Ubuntu is an open source OS,its possible to have something like that but i couldnt find it trough GUI.


Thanks

---

### Post by bonfido on 2009-12-27
[COLOR="Red"]Hint:[/COLOR] You must have Compiz installed before wishing to have different Backgrounds on each workspace!


**Here is the solution:**


1-Open up the terminal or press Alt+F2  and type *gconf-editor*


2-Along the tree menu Go to */apps/nautilus/preferences* and uncheck show desktop


3-Go to  compiz-manager and in the search box type wallpaper(you can  find it in utility section).


4-choose your preferred wallpapers according to the number of workspace you have(for example add 4 new if you have 4 workspace).


Enjoy

---

### Post by hawthornso23 on 2009-12-27
Is it still the case that icons are not drawn on the desktop if nautilus has `show desktop' disabled? I remember looking at this once before and deciding the increased prettiness was not worth the loss of functionality.

---

### Post by bonfido on 2009-12-27
> **hawthornso23 said:**
> Is it still the case that icons are not drawn on the desktop if nautilus has `show desktop' disabled? I remember looking at this once before and deciding the increased prettiness was not worth the loss of functionality.

Yes but you can have a nice dock on your desktop instead of icons.

---

### Post by mister_playboy on 2010-01-26
It's worth mentioning that Compiz can't handle any backgrounds that are more than 2048 pixels in height or width.  Instead of resizing them like Nautilus, you just get a white screen.

Resize them in a another program to <=2048 pixels, and then they will work.

---

### Post by dkjMusic on 2010-10-02
I use my desktop too much for downloads, works in progress, etc. to disable it for wallpaper.

How about this? I noticed that screenlets are workspace(WS)-independent; i.e., a screenlet placed on WS #1 doesn't show up on the other WS's. Is it possible to create a desktop-size background screenlet that would let you choose the image for the background? Might work, huh?

---

### Post by dkjMusic on 2010-10-05
> **dkjMusic said:**
> I use my desktop too much for downloads, works in progress, etc. to disable it for wallpaper.

How about this? I noticed that screenlets are workspace(WS)-independent; i.e., a screenlet placed on WS #1 doesn't show up on the other WS's. Is it possible to create a desktop-size background screenlet that would let you choose the image for the background? Might work, huh?

Never mind...I'm a dummy. Such a screenlet would hide the desktop.

---

### Post by malspa on 2010-10-05
Anyone know if GNOME 3 will be able to do this (with full functionality)?

---

