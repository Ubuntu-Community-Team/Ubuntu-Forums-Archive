---
title: "Installed with Wubi, how to boot with parameters?"
date: 2011-10-02
forum: General Help
---

### Post by denniskrq on 2011-10-02
I have installed 11.04 today on my PC with Wubi alongside my Win 7, I know that I have to boot with noapic parameter for my USB to work, and I can do that easily if I have installed Ubuntu into a separate partition. Now I can't set up after the initial installation with Wubi under Windows as I don't know how to boot with noapic parameter at the boot screen. So how can I do it?

---

### Post by bcbc on 2011-10-02
It's the same on Wubi (after the initial install) as it is with a normal partition install. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for details. Note - in post #1 it shows how to do this and says (Not Wubi) but in fact it's the same. For the Wubi specific initial boot, you can refer to post #8 but I don't think this is what you need.

---

### Post by denniskrq on 2011-10-03
Thx, that works and I got my Ubuntu up and running, now I've got a new problem. I'm trying to make the noapic parameter permanent by editing /boot/grub/menu.lst, but the problem is that the file is empty, it doesn't have anything in it. Now what do I do?

---

### Post by Rubi1200 on 2011-10-03
Ubuntu versions from 9.10 onwards no longer use the menu.lst but rather the conventions for GRUB2 which superseded legacy-GRUB.

You can follow the information here (sections 5 and 6) to edit the /etc/default/grub file:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

