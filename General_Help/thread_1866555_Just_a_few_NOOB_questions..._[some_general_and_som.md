---
title: "Just a few NOOB questions... [some general and some 11.10 related]"
date: 2011-10-21
forum: General Help
---

### Post by ksaul on 2011-10-21
Question 1: How do I figure out what programs command-line name is? I want to add programs to startup programs but do not know what they go by..

Question 2: How do I change/add/remove items from the top-panel-bar (where clock and running applications are -- using 11.10 64bit)? I tried right clicking on the bar itself, and alt+rightclick but not getting any menus...

Question 3: How do I change my screensaver, screen-off settings, etc.. on 11.10??

Question 4: I hate the 11.10 theme, and GNOME 3 icons for the panel on the left side - what are some themes I can download and where do I go to find more??

---

### Post by hwttdz on 2011-10-21
Question 1: How do I figure out what programs command-line name is? I want to add programs to startup programs but do not know what they go by..

One way is to add the launcher to the panel, then right click the launcher and look at the properties.  Another is to run a find command for desktop files i.e. "find / -xdev -iname "*.desktop" 2>/dev/null" and look at the text in the desktop files, pretty sure it's the exec line you want.  Both of these are annoying and it continues to bother me when documentation references the menu names instead of the real names.  I've spent entirely too long looking for programs in some cases.

The rest: I switched to xfce recently, because I find it more customizable and easier to work with than gnome 3.  So I could probably answer all of those in the xfce or gnome2 worlds, but I'm afraid I can be of no help here.

---

### Post by Larkspur on 2011-10-21
For question 1, you could go to /usr/share/applications in nautilus, right-click the icon you want and select properties.

---

### Post by ksaul on 2011-10-21
> **hwttdz said:**
> Question 1: How do I figure out what programs command-line name is? I want to add programs to startup programs but do not know what they go by..

One way is to add the launcher to the panel, then right click the launcher and look at the properties.


i wish i could do this, but i cant right click on the launcher or the top panel/bar =(



I am installing and going to try XFCE now, maybe I will enjoy this more then unity/gnome3 (wont be hard..)

---

### Post by cozumel on 2011-10-21
Various tweaks including desktop appearance, themes and screensaver

[THINGS TO TWEAK AFTER INSTALLING UBUNTU 11.10 ONEIRIC OCELOT]("http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html")

---

### Post by ksaul on 2011-10-21
> **Larkspur said:**
> For question 1, you could go to /usr/share/applications in nautilus, right-click the icon you want and select properties.

thank you this worked perfectly!!! :D

---

### Post by ksaul on 2011-10-21
> **cozumel said:**
> Various tweaks including desktop appearance, themes and screensaver

[THINGS TO TWEAK AFTER INSTALLING UBUNTU 11.10 ONEIRIC OCELOT]("http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html")

WOW!!! This is an awesome list!! thank you so much!!!

---

### Post by linuxinstalledfromhdd on 2011-10-21
That isn't the big list. 

This is the BIG list:
[URL="http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/"]
http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/[/URL]

Enjoy.

---

### Post by cozumel on 2011-10-21
Whoa!!  I was going to link to a couple of more lists but I think you have more than covered everything lol.

Bookmarked!

Thanks linuxinstalledfromhdd :)

---

### Post by ksaul on 2011-10-21
I am lost with all the tweaks I have applied, along with the new desktop environment(S) lol

xfce wasnt my cup of coffee, but I am on it now and going to see if I can get used to it.. I was happy to see I had an option for the Classic GNOME environment (not sure what I did to install that.....) and might revert to that if I dont like xfce.

Gnome Shell/GNOME 3 Desktop is VERY sexy imo, but the functionality just isnt there...

thank you for the new list for tweaks for 11.10 - going to see what else I can indulge my desktop with

---

### Post by linuxinstalledfromhdd on 2011-10-21
> **cozumel said:**
> Whoa!!  I was going to link to a couple of more lists but I think you have more than covered everything lol.

Bookmarked!

Thanks linuxinstalledfromhdd :)


You are welcome.  Stay thirsty my friend.

---

### Post by linuxinstalledfromhdd on 2011-10-21
You want sexy?  Install Lubuntu from the PPA in Ubuntu 10.10..  And strip it down to bare Openbox Desktop Environment.   Lubuntu >>> LXDE >>> down to Openbox..    Everything works great except the GDM login after selecting shutdown.  Use a nice Conky script and it is a head turner.

> **ksaul said:**
> I am lost with all the tweaks I have applied, along with the new desktop environment(S) lol

xfce wasnt my cup of coffee, but I am on it now and going to see if I can get used to it.. I was happy to see I had an option for the Classic GNOME environment (not sure what I did to install that.....) and might revert to that if I dont like xfce.

Gnome Shell/GNOME 3 Desktop is VERY sexy imo, but the functionality just isnt there...

thank you for the new list for tweaks for 11.10 - going to see what else I can indulge my desktop with

---

