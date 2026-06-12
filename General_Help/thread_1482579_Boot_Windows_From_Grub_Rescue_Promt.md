---
title: "Boot Windows From Grub Rescue Promt?"
date: 2010-05-13
forum: General Help
---

### Post by TwinTurbo on 2010-05-13
[CENTER][/CENTER]okay,i have dual booted ubuntu with windows. but after a few days i realized that ubuntu was too slow for my system and then decided to uninstall it and planned on installing it later. So i deleted the partitions on which ubuntu was installed. I rebooted the system and the grub rescue promt appeared, i already knew the work around was to restore the windows MBR using the live cd i used to install ubuntu or the Windows installer. But the main problem is my DVD suddenly stopped working . So my question is, can i boot windows using the promt? is there any commands? or can i uninstall grub using the rescue promt?


My desktop has been down for more that two weeks now so i hope someone can responed with an enlightening answer..hehe..Thanks in Advance Ubuntu Geeks!


Ubuntu version: 10.04

---

### Post by TwinTurbo on 2010-05-13
up ..

---

### Post by ba_saish on 2010-05-15
try these

rootnoverify (hd0,0)  {note: the second number after hd0 could be different depends on your installation) 
chainloader +1
makeactive
boot

[http://tuxthink.blogspot.com/2010/04/uninstall-linux.html](http://tuxthink.blogspot.com/2010/04/uninstall-linux.html)

---

