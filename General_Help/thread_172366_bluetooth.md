---
title: "bluetooth ??"
date: 2006-05-08
forum: General Help
---

### Post by Arabian Master on 2006-05-08
how i can use the bluetooth ??

when i used kubuntu it was simple but now in ubuntu i dont what to do :-k 

pleas help ](*,)

---

### Post by Arabian Master on 2006-05-08
hey what is rong nobody help me ??

---

### Post by chettyk on 2006-05-08
I don't know anything about Bluetooth but as a general rule the Ubuntu Wiki is a good place to seek information. For stuff about Bluetooth on Wiki have a look at:

[https://wiki.ubuntu.com/FrontPage?action=fullsearch&context=180&value=bluetooth&titlesearch=Titles](https://wiki.ubuntu.com/FrontPage?action=fullsearch&context=180&value=bluetooth&titlesearch=Titles)

---

### Post by exosyst on 2006-05-09
sudo apt-get install bluez-cups bluez-hcidump bluez-pcmcia-support bluez-pin bluez-utils gnome-bluetooth

Followed by executing:

gnome-bluetooth 

from a terminal. If you want to run it by default (i.e it appears in task tray, then consider adding it to your session programs under Preferences). I don't know why it's not setup nicely by default tho. Maybe a suggestion for dapper?

---

### Post by Efrain Valles on 2006-05-09
[QUOTE=exosyst]sudo apt-get install bluez-cups bluez-hcidump bluez-pcmcia-support bluez-pin bluez-utils gnome-bluetooth

Followed by executing:

gnome-bluetooth 

from a terminal. If you want to run it by default (i.e it appears in task tray, then consider adding it to your session programs under Preferences). I don't know why it's not setup nicely by default tho. Maybe a suggestion for dapper?[/QUOTE]

I have all the packages you mention. installed and my usb Bluetooth dongle still wont work :(, I tried gnome-bluetooth in terminal and it says that it is not a command,  any IDEA?

---

### Post by Loffe_ on 2006-05-19
[http://ubuntuforums.org/showthread.php?p=1031856](http://ubuntuforums.org/showthread.php?p=1031856)

---

