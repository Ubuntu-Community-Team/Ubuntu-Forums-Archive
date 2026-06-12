---
title: "Change the grub order"
date: 2006-03-07
forum: General Help
---

### Post by Compact on 2006-03-07
I have two HD, one, the master, with windows xp and the salve with ubuntu. When the computer starts, i see the grub screen and the default option is Linux. How can I change to XP? By the way, i cannot acces to ubuntu because I have a K8NF4G motherboard and nowadays is not compatible with linux 2.12 so i have to do it with windows or with the linux console.

---

### Post by twigilicious on 2006-03-07
Change the [FONT="Lucida Console"]default[/FONT] value in your menu.lst file (/boot/grub/menu.lst).

The items in the menu are at the bottom of the file and begin at 0. A default value of 0 refers to the first value in the list. 1 refers to the 2nd item in the list. Find your which item your Windows install is and subtract 1 to get the right default value.

---

### Post by aysiu on 2006-03-07
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

