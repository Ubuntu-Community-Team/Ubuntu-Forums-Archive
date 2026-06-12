---
title: "HELP!  need dependents list of libglib2.0"
date: 2011-02-27
forum: General Help
---

### Post by highspider on 2011-02-27
SOLVED 

I'm screwed.  How screwed had to boot the windows partition.

I destroyed libglib2.0 which destroyed the some 200+ dependentss.  basically the whole desktop and most the all operations. 

How did i do such a thing! I installed [GLib 2.28]("http://ftp.gnome.org/pub/gnome/sources/glib/2.28/") by building my own .deb which I didn't account for the dev ver also. which some how destroyed all its depends when I reinstalled glib ver ? the one in software channel.

~removed unneeded code~

Was wrong on depends list it didn't destroy them it just always updated  with new version which didn't allow the dev ver to work so the dependents of glib where unusable and i had to use  command line 
aptitude 
to downgrade it.  since I built the .deb package  exact it always considered it the newest version when removing and  reinstalling it.  grrr didn't recheck the version number.  can't believe  i loaded windows for this I should have just used lynx.

I wonder if you can lynx and use ubuntuforums yeah next project.

Solved

---

### Post by wiggly81 on 2011-02-27
the following link shows the direct dependents, and each has a link to a page that shows its dependents.

[http://packages.debian.org/sid/libglib2.0-0](http://packages.debian.org/sid/libglib2.0-0)

hope this is of some help.

---

### Post by highspider on 2011-02-27
Thanks you but i need underlying dependents not what libglib2.0 depends on.

when glib died everything underneath glib died not the whats above or what glib itself depends on.

---

