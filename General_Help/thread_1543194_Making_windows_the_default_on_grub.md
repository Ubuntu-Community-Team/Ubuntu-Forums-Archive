---
title: "Making windows the default on grub"
date: 2010-07-31
forum: General Help
---

### Post by cufflink87 on 2010-07-31
Hi, I would like to make my windows the default OS on the list.

I tried following these instructions:
[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

However, sudo gedit /boot/grub/menu.lst opens up a blank file, and I can't even find the file when I follow the path

Please help

---

### Post by Mi11z on 2010-07-31
> **cufflink87 said:**
> Hi, I would like to make my windows the default OS on the list.

I tried following these instructions:
[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

However, sudo gedit /boot/grub/menu.lst opens up a blank file, and I can't even find the file when I follow the path

Please help

Install this (.deb packages) and use google translate, once installed click install burg and the next (parameters) box there will be an option to select what ever you want from the windows loader kernel to the ubuntu gnu/linux ones plus burg will make your grub boot loader look nice too. :)

Here:

[http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice/](http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice/)

and i admit there is a more simpler direct solution for your exact query but this is the way i do it and thus was easier to tell you straight away hopefully someone else will reply with a more direct solution for you. :) :D

---

### Post by Raymond2201 on 2010-07-31
Ubuntu search is your friend

[http://ubuntuforums.org/showthread.php?t=1309890](http://ubuntuforums.org/showthread.php?t=1309890)

---

### Post by howefield on 2010-07-31
> **cufflink87 said:**
> sudo gedit /boot/grub/menu.lst opens up a blank file

Presumably you have a recent version of Ubuntu which uses Grub2, and doesn't have a menu.lst, hence the blank file.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

