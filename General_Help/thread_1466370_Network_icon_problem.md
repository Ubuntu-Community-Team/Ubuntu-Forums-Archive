---
title: "Network icon problem"
date: 2010-04-30
forum: General Help
---

### Post by mallorcaben on 2010-04-30
Thinkpad T41
[Ubuntu 9.10]("https://help.ubuntu.com/9.10/index.html")

I am new to Linux although I am very experienced with Windows and Mac OS.
The network icon on the top panel disappeared. At the moment it shows 2 bluetooth icons, but sometimes it shows 2 sound icons.
One icon is clickable, but the one that has replaced my network icon is not.
I installed Ubuntu earlier this week and had the same problem, this is the 3rd re install.
When I first install, the network icon (wireless) shows, but after a restart, it is gone, replaced by another.
It does not seem to affect my internet connection. I am connected to my router fine.
As a noob to the whole Linux thing, please can anybody help.
regards
Benjamin

---

### Post by dino99 on 2010-04-30
as you are a Mac user, ubuntu is very close, might not be a problem.

seem there are broken settings left behind. into a terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by mallorcaben on 2010-04-30
Dino,
I did as you instructed and so far so good after reboot.
Many thanks for your quick reply.
Benjamin

---

### Post by mallorcaben on 2010-04-30
bugger, switched on a few hours later and its gone again!
Any ideas peeps?

---

