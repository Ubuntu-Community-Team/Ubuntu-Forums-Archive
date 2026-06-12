---
title: "Why am I seeing the wrong boot logo?"
date: 2006-03-20
forum: General Help
---

### Post by grendel_khan on 2006-03-20
Running Ubuntu Breezy (5.10). I apt-get installed kubuntu-desktop some time back, and it set my boot logo to the 'kubuntu' one. I want to change it back to the regular 'ubuntu' boot logo and color scheme; do I have to uninstall KDE to do this? I want to still use some KDE applications (k3b, for instance), but I use gnome as my desktop environment now. How and where is the boot logo set?

---

### Post by sands on 2006-03-20
I think u have selected the KDM during installation..
To restore gnome thing
use thi cmd
sudo dpkg-reconfigure gdm

---

### Post by sands on 2006-03-20
Select GDM from the list
GDM
KDM

---

### Post by ssam on 2006-03-20
this might be what you are after [http://ubuntuforums.org/showthread.php?t=113250](http://ubuntuforums.org/showthread.php?t=113250)

you dont need all of kubuntu installed to run kde programs, usually just qt and the kde libraries. synaptic will make sure the you have everything you need installed to run a program.

---

### Post by Beowolf on 2006-03-20
Is it really a GDM issue? I use xubuntu on my box, and when you install that on top of the existing ubuntu-desktop, the boot image is changed to xubuntu even though you are not changing your GDM configuration. ??

---

### Post by claes on 2006-03-20
It's not gdm fault. It's kdm or xdm that's being set to be the display manager when they are installed after gdm.

Claes

---

### Post by chronusdark on 2006-03-20
i believe the issue he is talking about is the usplash boot screen which i had the same problem and what i did was remove kubuntu-artwork-usplash <or something like that> and then when i did a kernel update it was back to normal

---

