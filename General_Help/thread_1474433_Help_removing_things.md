---
title: "Help removing things"
date: 2010-05-06
forum: General Help
---

### Post by jakari on 2010-05-06
Hey

I have been using ubuntu for a wile now and am loving it, i started showing it to my friends and because of this I thought it would be a good idea to have a portable version.

I have installed a Wubi install to my 8GB USB stick and have it all working and booting fine

and now my friend wants to do the same but instead of using it as his main portable OS he just wants it so he can run virtualbox and have it run XP

so he wants me to uninstall/Remove a lot of the ubuntu things he doesn't need but I'm not to sure what I can get rid of that would maximise the space for his XP drive/install.

Could anyone give me a few things that would be taking up alot of space that I can remove for him?

Thanks

---

### Post by koanhead on 2010-05-06
It's problematic to go removing things, since it's hard to know what might get broken due to dangling dependencies and other weirdness. I've had apt-get try to remove xserver-xorg when I was only trying to get rid of mysql server or some such thing (I don't remember exactly, and never posted about it).
A better solution might be to use the Ubuntu Server image:

[http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)

Make his usb stick boot the server edition, then install virtualbox (or xen or qemu or whatever you want) and whatever else you need piece by piece.

---

### Post by jakari on 2010-05-06
Thanks for the info i will give the Server image a try :)

---

### Post by Famicommie on 2010-05-06
Ubuntu is meant to be a full desktop experience, and can't really be condensed down too much. The biggest single space offender is openoffice.org and even that only takes up like 200 MiB. Instead you might want to install [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

It's based on Ubuntu, but is intentionally pared down.

---

