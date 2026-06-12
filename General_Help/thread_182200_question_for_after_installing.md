---
title: "question for after installing"
date: 2006-05-25
forum: General Help
---

### Post by knewmocker on 2006-05-25
I had tried to get the live version on Ubuntu to work on my pc but I encountered problems with but I still wanted to try it. I never had two OS on my computer at once and was wondering if after I installed it would my computer boot up into Ubunto or would it go to Windows xp. If it will boot up in Ubuntu how can I change that.

---

### Post by bruce89 on 2006-05-25
It will give a menu on boot asking which you want each time.

---

### Post by johnc4510 on 2006-05-25
Toward the end of the install it should ask you to:set up the grub. Select yes
Then after the install, when you boot, it will give you the grub menu. From that you select Ubuntu or any other OS listed.

---

### Post by oldmanstan on 2006-05-25
Typically the installers will make whatever linux version you are installing the default. it will present you with a menu (as mentioned already) where you can choose which OS to boot into but if you do not make a selection within a certain time period (usually around 30 seconds) it will default into linux.

but you can change this by editing a text file (can't remember that path and i'm on a windows box right now, if no one else posts it i will post it later when i get home)

---

### Post by Ramses de Norre on 2006-05-25
sudo gedit /boot/grub/menu.lst ;)

---

