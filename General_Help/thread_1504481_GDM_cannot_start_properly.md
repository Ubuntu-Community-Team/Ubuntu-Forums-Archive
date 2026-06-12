---
title: "GDM cannot start properly"
date: 2010-06-08
forum: General Help
---

### Post by TheDesertDragon on 2010-06-08
I'm in quite a panic right now. I need to use my Linux system for school work but I can't, because it has stopped working.

Yesterday I installed the new Linux header files and new OOo updates and restarted this morning, and now the Xserver refuses to start. It simply gets to rendering the gnome paneels and then locks up.

I can then go into the terminals, where a message will me that "/etc/timidity" is not a proper homefolder - but that is not my homefolder, and typing ls reveals my regular homefolder by default.

I don't get any sort of error report or anything like that, and I am no expert.
Help? =(

---

### Post by dino99 on 2010-06-08
into a console:

sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm

---

### Post by TheDesertDragon on 2010-06-08
Thank you, but that didn't change anything at all. I still get the same problem and nothing has changed about gdm.

---

### Post by TheDesertDragon on 2010-06-08
Guys I really need some help here! :(

I managed to get into Gnome in failsafe mode.
This meant I ran low graphics and that the system actually ran fine otherwise.

The only problem was that the gnome panels are irrepairably dead. If I restart the gnome-panels shell the panel will render 10 shortcuts, then die and start flickering once it has to render the Ubuntu main menu. (The custom one with the 3 submenus)

This also means I cannot use alt+F2 to start up programs because... no panels. I can't get on the internet because I don't know how to get on it using a terminal, and the only reason I even managed to get on my terminal was because I opened a folder to get into Nautilus and then found the gnome-terminal program in etc and launched it directly. :P

I really, really need a way to purge and reinstall the gnome panels without internet.

---

