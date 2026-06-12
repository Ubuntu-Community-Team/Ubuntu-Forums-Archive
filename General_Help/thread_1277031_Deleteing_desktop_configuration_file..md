---
title: "Deleteing desktop configuration file."
date: 2009-09-27
forum: General Help
---

### Post by mickmouse13 on 2009-09-27
Hey I have spent today playing with ubuntu and  a lot of its things i need to learn, through a manual install and adding something manual to the applications bar using

[http://www.ehow.com/how_5355552_add-package-applications-button-menu.html](http://www.ehow.com/how_5355552_add-package-applications-button-menu.html)

this i did this 5times due to the application not being fully installed. I figured it all out and everything is in order, but i have an extra icon in the applications window "other/camodo" (i misspelled komodo) i went to usr/share/applications and clicked the .desktop file and hit delete... it said i did nto have permission... so i used "sudo apt-get remove /usr/share/applications/Kamodo.desktop" again it and i got this message(with the command) 

mick@mick-desktop:~$ sudo apt-get remove /usr/share/applications/Kamodo.desktopReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 


i just want this off of my app list. if anyone is willing to help its appreciated and im still a noob so try to keep it SEMI simple =) loving ubuntu and im useing 9.4 if thats important.

---

### Post by skatinjj on 2009-09-27
right click your applications menu and click Edit menus

from there navigate to where komodo is, right click and click delete

sorry for the quick response if you need further help just ask.....got dinner cooking lol

---

### Post by Tamalin on 2009-09-27
Well, komodo isn't in the repository and you don't want to uninstall it, so i don't think apt-get is what you want to be using.  Why dodn't you use

```
sudo rm /usr/share/applications/Komodo.desktop
```
if you just want to delete the file?  I won't uninstall the package, but it will delete the shortcut. :)

> **skatinjj said:**
> right click your applications menu and click Edit menus

from there navigate to where komodo is, right click and click delete

sorry for the quick response if you need further help just ask.....got dinner cooking lol
(or do this if you want to go by way of GUI)

---

### Post by kryos on 2009-09-27
Right click applications.  Select edit menus/other and un-check camodo?

---

### Post by mickmouse13 on 2009-09-27
wow. that was very fast, thanks a lot all of you. I got it fixed.

---

