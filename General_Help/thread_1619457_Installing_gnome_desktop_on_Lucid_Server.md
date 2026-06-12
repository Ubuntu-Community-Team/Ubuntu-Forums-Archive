---
title: "Installing gnome desktop on Lucid Server"
date: 2010-11-11
forum: General Help
---

### Post by pharubu on 2010-11-11
I have installed the desktop on top of the server;
however I end up with a brown looking 
skin and no sub menus.

How do I get the new skin and sub menus ?

Installed ubuntu-10.04-server-i386.iso on Sun VirtualBox

Ran the following commands:

apt-get install ubuntu-desktop
apt-get install gdm
/etc/init.d/gdm start
dpkg-reconfigure xserver-xorg

xstart

apt-get update
apt-get -u upgrade 

I can get the various menu options by running 
the following commands.

apt-get install gnome-terminal
apt-get install gedit
apt-get install synaptic

But there must be a single command which installs all
the standard menus ?

Thanks

---

### Post by pharubu on 2011-06-22
Answer to my own question 

sudo -i
apt-get update
apt-get install linux-headers-$(uname -r) build-essential ubuntu-desktop
startx

shutdown now -h

------

Ctrl-Alt-F1 to F6 (Goes to terminal)
Ctrl-Alt-F7 (Goes back to GUI)

------

Load Terminal instead of GUI on start up

System, Administration, Services 
  un-check gdm

---

