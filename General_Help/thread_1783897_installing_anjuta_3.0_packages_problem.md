---
title: "installing anjuta 3.0 packages problem"
date: 2011-06-16
forum: General Help
---

### Post by nickos on 2011-06-16
so i downloaded anjuta 3.0.3.0.tar.bz2 followed the instactions then typed ./configure and heres what i got after many lines of code

configure: error: Package requirements (gthread-2.0 >= 2.22.0
    glib-2.0 >= 2.28.0
    gio-2.0 >= 2.28.0
    gtk+-3.0 >= 3.0.0
    gdk-pixbuf-2.0 >= 2.0.0) were not met:

No package 'gtk+-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


how do i install these packages?
my ubuntu version is 11.04

---

### Post by nothingspecial on 2011-06-16
I would think that is because Ubuntu 11.04 is using gtk2 where as the brand new anjunta depends on gtk3

---

### Post by nickos on 2011-06-16
arg,what should i do now?i have to work with anjuta 3 instead of anjuta 2 ...there must be a way but im with linux for about 2 months i only know the basic terminal comands :/

---

### Post by nothingspecial on 2011-06-16
You could install gnome 3 and gnome shell which runs fine over a xubuntu install (I'm using it on my netbook), but I believe there are a few issues if you try to install it over unity.

Another option would be to run a distro that ships with gnome 3 (fedora is one)

Someone else probably knows better than me.

---

### Post by nickos on 2011-06-16
im using ubuntu 11.04 classic,but i would be greatful if somebody can post a solution here. :) :) :) :)

---

### Post by nickos on 2011-06-16
please,can somebody help?

---

### Post by nickos on 2011-06-16
FAIL!I downloaded gnome 3 for my 11.04 and its all messed up and nothings working!

What to do?????
install 10.14 and use anjuta 3.0? 


HELp!

---

### Post by nickos on 2011-06-17
oke,so i now have ubuntu 10.10 after reinstalling .

tips?

---

### Post by nothingspecial on 2011-06-17
Well I would have installed xubuntu 11.04. It doesn't conflict with gnome 3 like Ubuntu does.

Apparently Gnome 3 is even more of a pita with 10.10

---

### Post by Cybolic on 2011-07-14
This worked for me:

```

sudo apt-get install aptitude
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo aptitude install anjuta
sudo rm /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
sudo apt-get update

```

It adds the Gnome3 PPA, installs anjuta and then removes the PPA again.
Just say yes to what aptitude recommends; it might suggest removing devhelp, so you might have to live without that.

I think I might have installed the Gtk3 package from the Elementary PPA, so that might be different for you.

---

