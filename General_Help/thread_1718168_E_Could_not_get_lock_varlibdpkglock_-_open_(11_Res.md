---
title: "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable"
date: 2011-03-30
forum: General Help
---

### Post by kkyod on 2011-03-30
im getting this error in terminal and just want to sudo apt-get some stuff and have restarted my comp it is a acer aspire one

---

### Post by sikander3786 on 2011-03-30
Welcome to the forums :-)

Reboot once more and if the error persists, follow this command.

```
sudo rm /var/lib/dpkg/lock
```

```
sudo apt-get update
```

---

### Post by kkyod on 2011-03-30
can you tell me what these commands do i want to try to billed  my own distro for personal use but ima noob

---

### Post by kkyod on 2011-03-30
i also keep getting this what does it mean and what could cause it

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

---

### Post by kkyod on 2011-03-30
zachary@adam-book:~$ sudo apt-get install bisigi-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tumbler libjpeg8 tumbler-common libthunarx-2-0 xscreensaver linux-headers-2.6.35-22 libgarcon-1-0
  linux-headers-2.6.35-22-generic libgarcon-common libtumbler-1-0 thunar-data libjpeg-progs xfdesktop4-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  airlines-theme aquadreams-theme balanzan-theme bamboo-zen-theme bisigi-cursor-theme eco-theme ellanna-theme
  emerald-aquadreams-theme emerald-bamboo-zen-theme emerald-exotic-theme emerald-infinity-theme emerald-orange-theme
  emerald-showtime-theme emerald-step-into-freedom-theme emerald-tropical-theme emerald-ubuntu-sunrise-theme
  emerald-wild-shine-theme exotic-theme gnome-airlines-theme gnome-aquadreams-theme gnome-balanzan-theme
  gnome-bamboo-zen-theme gnome-eco-theme gnome-ellanna-theme gnome-exotic-theme gnome-infinity-theme gnome-orange-theme
  gnome-showtime-theme gnome-split-theme gnome-step-into-freedom-theme gnome-tropical-theme gnome-ubuntu-sunrise-theme
  gnome-wild-shine-theme gtk-airlines-theme gtk-aquadreams-theme gtk-balanzan-theme gtk-bamboo-zen-theme gtk-eco-theme
  gtk-ellanna-theme gtk-exotic-theme gtk-infinity-theme gtk-orange-theme gtk-showtime-theme gtk-split-theme
  gtk-step-into-freedom-theme gtk-tropical-theme gtk-ubuntu-sunrise-theme gtk-wild-shine-theme icon-airlines-theme
  icon-aquadreams-theme icon-balanzan-theme icon-bamboo-zen-theme icon-eco-theme icon-ellanna-theme icon-exotic-theme
  icon-infinity-theme icon-showtime-theme icon-split-theme icon-step-into-freedom-theme icon-tropical-theme
  icon-ubuntu-sunrise-theme icon-wild-shine-theme infinity-theme metacity-airlines-theme metacity-aquadreams-theme
  metacity-balanzan-theme metacity-bamboo-zen-theme metacity-eco-theme metacity-ellanna-theme metacity-exotic-theme
  metacity-infinity-theme metacity-orange-theme metacity-showtime-theme metacity-split-theme
  metacity-step-into-freedom-theme metacity-tropical-theme metacity-ubuntu-sunrise-theme metacity-wild-shine-theme
  orange-theme showtime-theme split-theme step-into-freedom-theme tropical-theme ttf-mscorefonts-installer
  ubuntu-sunrise-theme wallpaper-airlines-theme wallpaper-aquadreams-theme wallpaper-balanzan-theme
  wallpaper-bamboo-zen-theme wallpaper-eco-theme wallpaper-ellanna-theme wallpaper-exotic-theme wallpaper-infinity-theme
  wallpaper-orange-theme wallpaper-showtime-theme wallpaper-split-theme wallpaper-step-into-freedom-theme
  wallpaper-tropical-theme wallpaper-ubuntu-sunrise-theme wallpaper-wild-shine-theme wild-shine-theme
The following NEW packages will be installed:
  airlines-theme aquadreams-theme balanzan-theme bamboo-zen-theme bisigi-cursor-theme bisigi-themes eco-theme ellanna-theme
  emerald-aquadreams-theme emerald-bamboo-zen-theme emerald-exotic-theme emerald-infinity-theme emerald-orange-theme
  emerald-showtime-theme emerald-step-into-freedom-theme emerald-tropical-theme emerald-ubuntu-sunrise-theme
  emerald-wild-shine-theme exotic-theme gnome-airlines-theme gnome-aquadreams-theme gnome-balanzan-theme
  gnome-bamboo-zen-theme gnome-eco-theme gnome-ellanna-theme gnome-exotic-theme gnome-infinity-theme gnome-orange-theme
  gnome-showtime-theme gnome-split-theme gnome-step-into-freedom-theme gnome-tropical-theme gnome-ubuntu-sunrise-theme
  gnome-wild-shine-theme gtk-airlines-theme gtk-aquadreams-theme gtk-balanzan-theme gtk-bamboo-zen-theme gtk-eco-theme
  gtk-ellanna-theme gtk-exotic-theme gtk-infinity-theme gtk-orange-theme gtk-showtime-theme gtk-split-theme
  gtk-step-into-freedom-theme gtk-tropical-theme gtk-ubuntu-sunrise-theme gtk-wild-shine-theme icon-airlines-theme
  icon-aquadreams-theme icon-balanzan-theme icon-bamboo-zen-theme icon-eco-theme icon-ellanna-theme icon-exotic-theme
  icon-infinity-theme icon-showtime-theme icon-split-theme icon-step-into-freedom-theme icon-tropical-theme
  icon-ubuntu-sunrise-theme icon-wild-shine-theme infinity-theme metacity-airlines-theme metacity-aquadreams-theme
  metacity-balanzan-theme metacity-bamboo-zen-theme metacity-eco-theme metacity-ellanna-theme metacity-exotic-theme
  metacity-infinity-theme metacity-orange-theme metacity-showtime-theme metacity-split-theme
  metacity-step-into-freedom-theme metacity-tropical-theme metacity-ubuntu-sunrise-theme metacity-wild-shine-theme
  orange-theme showtime-theme split-theme step-into-freedom-theme tropical-theme ubuntu-sunrise-theme
  wallpaper-airlines-theme wallpaper-aquadreams-theme wallpaper-balanzan-theme wallpaper-bamboo-zen-theme
  wallpaper-eco-theme wallpaper-ellanna-theme wallpaper-exotic-theme wallpaper-infinity-theme wallpaper-orange-theme
  wallpaper-showtime-theme wallpaper-split-theme wallpaper-step-into-freedom-theme wallpaper-tropical-theme
  wallpaper-ubuntu-sunrise-theme wallpaper-wild-shine-theme wild-shine-theme
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 101 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
zachary@adam-book:~$ 


Help someone please

---

### Post by sikander3786 on 2011-03-31
Make sure you are not running 2 or more package manager simultaneously i.e, apt-get, aptitude, Software Center, Update Manager, Synaptic Package Manager, Jockey etc.

A reboot will be better to start the proceedings. Then remove the other lock file causing problems.

```
sudo rm /var/cache/apt/archives/lock
```

Now post the output of following command. It would try to repair any broken or un-configured packages.

```
sudo dpkg --configure -a
```

We'll need to see the complete output please.

---

