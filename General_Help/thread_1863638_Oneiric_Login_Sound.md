---
title: "Oneiric Login Sound"
date: 2011-10-18
forum: General Help
---

### Post by bvill on 2011-10-18
I am running 64 bit Oneiric on a clean install.  Most things are functioning correctly but I lost my Gnome login sound, which I like.  It was working until a couple of days ago but I inadvertently changed some setting that is blocking the default theme from loading.  All sound files seem to be fine and in place.  If I login as guest the login sound plays fine but when I login to my account it is silent at login.  If I try to run the Gnome login command in terminal it says file not found.  There must be a simple tweak to fix this that I am not seeing.  I would really appreciate any suggestions as to what to look for.  I don't want to reinstall for something that should be simple to correct.  Thanks.

---

### Post by bvill on 2011-10-18
Deleted .dconf in home folder and started over...should have thought of that first.  Sometimes the simplest things are the most elusive.

---

### Post by sant on 2011-10-19
Same problem  here. Your workaround was the solution for me.
Thanks for sharing it.

---

### Post by topdownjimmy on 2011-10-29
Rather than deleting the whole .dconf folder, just open dconf-editor and navigate to:


  org.gnome.desktop.sound
  

Change the value of "theme-name" to "ubuntu"
  

Also check to make sure that "GNOME Login Sound" is checked in "Startup Applications".
  

I've also filed a bug about this:
[http://pad.lv/883677](http://pad.lv/883677)

---

### Post by gacb on 2012-03-30
Thanks - changing from 'freedesktop' to 'ubuntu' restored a host of missing sounds.

---

