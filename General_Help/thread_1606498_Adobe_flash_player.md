---
title: "Adobe flash player"
date: 2010-10-26
forum: General Help
---

### Post by Lonewolf-LRS- on 2010-10-26
i am very new to linux.  i have read how to install adobe found the mozilla/plugins like it said.  but when i try to move the libflashplayer.so file to the plugins folder it says i dont have permission to change the folder cause i am not the owner. it says the owner is Root.  any ideas?

---

### Post by gandaran on 2010-10-26
use the system repositories to install the flash plugin, look in ubuntu software center or synaptic for 'flashplugin-installer'.
or use the command line to install, open terminal and type
```
sudo apt-get install flashplugin-installer
```
easy!

---

### Post by oldos2er on 2010-10-26
> **gandaran said:**
> use the system repositories to install the flash plugin

Unless you're running 64-bit Ubuntu and you want the latest 64-bit flash.

---

### Post by lovinglinux on 2010-10-26
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture. It allows to choose between the regular 32bit and the 64bit preview if you are on a 64bit system. Keep the extension updated and you will receive alerts when a new preview version is available to be installed.

I'm the developer btw.

---

### Post by Lonewolf-LRS- on 2010-10-26
gandaran<  i did get it installed from the ubuntu software center ty
oldos2er< it is the 64bit version of ubuntu
lovinglinux< when i use it on hulu the player works until you go full screen is it because of the version of flash have? if so how do i see if i have the 64 or the 32 bit

Thanks for yalls help

---

### Post by lovinglinux on 2010-10-26
> **Lonewolf-LRS- said:**
> gandaran<  i did get it installed from the ubuntu software center ty
oldos2er< it is the 64bit version of ubuntu
lovinglinux< when i use it on hulu the player works until you go full screen is it because of the version of flash have? if so how do i see if i have the 64 or the 32 bit

Thanks for yalls help

I can't access Hulu here, but there is a recent big thread about it somewhere in the forum.

---

