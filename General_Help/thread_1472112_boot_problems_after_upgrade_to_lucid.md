---
title: "boot problems after upgrade to lucid"
date: 2010-05-04
forum: General Help
---

### Post by behzadsh on 2010-05-04
hi,
I've just upgrade ubuntu from Karmic to Lucid.
I followed every step in [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) everything is fine except three things.

[LIST=1]
[*]in GNU GRUB there are 3 different boot for ubuntu, two with Linux 2.6.32-21-generic and a 2.6.32-14-generic, plus their recovery mode
[*]it takes so long to view ubuntu logo and start booting (long time a black screen with a cursor blinking)
[*]an error appear in boot that "**An error occurred while mounting /proc/bus/usb**"
[/LIST]
thank for support :)

---

### Post by dcstar on 2010-05-04
> **behzadsh said:**
> hi,
I've just upgrade ubuntu from Karmic to Lucid.
I followed every step in [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) everything is fine except three things.

[LIST=1]
........
[*]an error appear in boot that "**An error occurred while mounting [B]/proc/bus/usb**[/B]"
[/LIST]
thank for support :)

That is not supported in 10.04, remove it from your /etc/fstab file.

---

### Post by behzadsh on 2010-05-04
> **dcstar said:**
> That is not supported in 10.04, remove it from your /etc/fstab file.

thanks dcstar.
what about the other issues?

---

### Post by dino99 on 2010-05-04
go ahead, dont worry

be sure your sources.list only have genuine lucid repo ( no more karmic or else, no ppa or third party activated)

then update 
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

install gconf-cleaner and use it (yes to all)
can install bleachbit to make room

---

### Post by behzadsh on 2010-05-04
> **dino99 said:**
> go ahead, dont worry

be sure your sources.list only have genuine lucid repo ( no more karmic or else, no ppa or third party activated)
.....
install gconf-cleaner and use it (yes to all)
can install bleachbit to make room

thanks alot, hope it work ;)

------------
but it does not work, there are still 3 different boot
------------

I used gconf-cleaner once again and it fixed, thanks for help

---

