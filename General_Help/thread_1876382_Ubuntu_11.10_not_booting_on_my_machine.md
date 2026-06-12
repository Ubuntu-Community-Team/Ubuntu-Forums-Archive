---
title: "Ubuntu 11.10 not booting on my machine"
date: 2011-11-06
forum: General Help
---

### Post by lucipacurar on 2011-11-06
Hi everyone,

I have installed Ubuntu 11.10 on my machine (Gigabyte EP45-UD3, Core 2 Duo E8400, 8800GT 512MB) and at the first boot I got a screen like this one:

[[IMG]http://img542.imageshack.us/img542/3616/ubuntu.th.jpg[/IMG]](http://imageshack.us/photo/my-images/542/ubuntu.jpg/)

Hitting Ctrl+Alt+Del started killing processes and rebooted. It worked fine the second time, I installed some updates, but since then I couldn't boot into ubuntu anymore. It hangs at the same screen and sometimes some services in the image above fail to start. The thing that seems odd is that sometimes is shows more services there, sometimes one fails to load, but still I can't boot.

Does anybody have and ideea why?

Best,
Lucian

PS: this is the first time I get boot problems with ubuntu :)

---

### Post by shvnrrthn on 2011-11-30
I encountered this problem too. I installed ubuntu 11.10 for more than a month and it was working perfectly until now. Suddenly when I boot up I get the same screen you got. I don't know what's wrong or what to do D: 

Anyone able to solve this prob? Please.

---

### Post by stalkingwolf on 2011-11-30
when grub opens choose the second selection ( repair) after it runs a second window will pop up choose repair broken packages

myself id turn off the auto report thing to.

---

### Post by sirvinniei on 2011-11-30
also maybe the new update brought a updated linux kernel.
the grub may be reversed, have you set your grub to your preferences (like nomodeset)

---

### Post by shvnrrthn on 2011-12-01
I managed to boot back ubuntu by typing in **sudo gdm**
and then open terminal and type in **sudo nano /etc/default/apport** and set the value to 1. Everything works fine now :D

---

### Post by lucipacurar on 2011-12-21
Another reinstall solved the problem for me. But the next set of updates broke the wireless connectivity. I have a TP-Link TL-WN951N card which now refuses to connect to my home WLAN.

---

