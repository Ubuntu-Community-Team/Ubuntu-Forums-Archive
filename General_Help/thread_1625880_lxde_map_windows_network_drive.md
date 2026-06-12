---
title: "lxde map windows network drive"
date: 2010-11-19
forum: General Help
---

### Post by LuniTux on 2010-11-19
Hello,

I have an Ubuntu 9.10 customized computer and I need it to be able to map to windows xp computers on our network. I installed ubuntu mini as the default OS, then:

sudo apt-get install xorg lxde ldm network-manager-gnome gcc samba linux-headers-`uname -r`firefox thunderbird xorg

(I may have missed one or two)

I have a fully functional desktop and can access the internet via network-manager-gnome. Is there any other way to connect to the network other than gigolo (keeps asking for password even when password is correct) or nautilus?

If there is a way to remove pcmanfm (was installed with lxde) and install nautilus or to hide pcmanfm and use nautilus that would be ok as well.

---

### Post by LuniTux on 2010-11-23
Hello Me.

I descided to go with smbfs and mount for a command line connection instead of a gui tool that does not seem to work correctly

---

