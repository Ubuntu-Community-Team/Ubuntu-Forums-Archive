---
title: "Convert from KDE to Gnome?"
date: 2006-04-18
forum: General Help
---

### Post by wreckingcru on 2006-04-18
I installed Kubuntu and not particularly thrilled with KDE (it's a little too....BLUE)

How can I switch to Gnome without re-installing the OS? I have some useful data on my comp that I'd rather not lose.

Thanks!

---

### Post by davebgimp on 2006-04-18
You know you can install themes and change KDE's color to whatever you want right?

Anyway, to install Gnome:
sudo apt-get install ubuntu-desktop

---

### Post by aysiu on 2006-04-18
Go to KMenu > System > Konsole and type ```
sudo apt-get update
``` [QUOTE=davebgimp]
Anyway, to install Gnome:
sudo apt-get install ubuntu-desktop[/QUOTE] Log out. Click on **Session** and select **Gnome**. Log back in.

To change KDE's colors, press Alt-F2 and type ```
kcontrol
``` Expand the first tree menu and go to **Colors**.

---

### Post by foof on 2006-04-19
If I do this, does it mean I am running Ubuntu instead of Kubuntu then?
..or are there any differences left?

---

### Post by aysiu on 2006-04-19
[QUOTE=foof]If I do this, does it mean I am running Ubuntu instead of Kubuntu then?
..or are there any differences left?[/QUOTE] If you add ubuntu-desktop, you're *adding* to, not replacing, kubuntu-desktop, so you'll have both, and you can choose before you log in which you want to use.

---

