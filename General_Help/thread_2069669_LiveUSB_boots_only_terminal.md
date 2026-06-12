---
title: "LiveUSB boots only terminal"
date: 2012-10-11
forum: General Help
---

### Post by han5vk on 2012-10-11
Hello, I have created a liveUSB of Ubuntu 11.10. It works well on my home computer, after selecting Ubuntu in GRUB it loads on and runs. But, when I put the USB into school computer, it loads GRUB, then I choose ubuntu 11.10 and it starts loading. But, it does not boot into a graphical interface, with the login screen, but only gives me a terminal line on a black screen. Why is it not working on school computer as well as on mine? Is it because of different graphics drivers? Thanks for help.

---

### Post by bart.a on 2012-10-11
are you using the server version? That is without GUI (graphical user interface)

---

### Post by han5vk on 2012-10-11
Well, no. On my computer, it runs GUI, wndows, Unite, everything. So, it sure is not server version. Just on this, school computer, it loads up just the terminal. I have no idea why is it doing so.

---

### Post by bart.a on 2012-10-11
maybe you can try reinstalling the GUI via the terminal.. 

[I]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop[/I]

---

### Post by clay7 on 2012-10-11
I've experienced this too, and unfortunately so far I don't have a good solution. I don't mean the following to be technical advice...it's just my experiences.

As far as I can tell, if the USB drive has any kind of persistence, it remembers the graphical settings of the computer it was last used on. Then, if the USB drive is used on a different computer with different graphics drivers, the end result is the server-style logon: black screen with white text.

My workaround is to use a Live DVD and save working files to a USB drive. If anyone has a better solution, please post :)

---

