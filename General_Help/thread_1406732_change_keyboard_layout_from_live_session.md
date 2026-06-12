---
title: "change keyboard layout from live session??"
date: 2010-02-14
forum: General Help
---

### Post by selahlynch on 2010-02-14
I need to change my keyboard layout from Arabic to USA.  I cannot login to my machine, however I can access its files via a live session.

Is there a text file I can edit that will change my keyboard layout.

I am running Ubuntu 8.10 with a Gnome desktop.

I have tried editing /etc/X11/xorg.conf and this did not work.

---

### Post by rnerwein on 2010-02-14
hi
i think the way to do this is:
right klick at the upper pannel.
select add to panel.
then choose "keyboard layout" ( i've installed german language hope my english translation is right).

this works for me to switch from "german" to "thai"
i know the problem with login in thai  :-)

ciao

oh i forgot: i am running karmic koala 9.10 and have two keyboards connected. one german and one thai --> works !

---

### Post by selahlynch on 2010-02-14
I cannot do what you said because I cannot log into my computer!  This is because my keyboard is set to arabic, but my username is in English.

This is the reason I am having difficulty.

I need to change my keyboard layout but I dont think I can do it graphically by clicking and such.

I am running a live session on my computer, and I can access all my files.  I am hoping to find a text configuration file that I can edit.

Any help will be VERY VERY appreciated!!

---

### Post by selahlynch on 2010-02-14
Al Hamduliallah!!!!!

It is fixed!!!!

While running a live session on my computer I found the following file on the harddrive of my computer:
/media/97GBdrive/etc/default/console-setup

I edited
XKBMODEL="pc105"
XKBLAYOUT="us"

I rebooted and was able to login with US characters.

I think for previous versions of Ubuntu, one could edit the xorg.conf file, but for Ubuntu 8.10 editing that file did nothing.

Hooray :)

---

