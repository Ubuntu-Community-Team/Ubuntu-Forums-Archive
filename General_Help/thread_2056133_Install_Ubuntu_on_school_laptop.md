---
title: "Install Ubuntu on school laptop"
date: 2012-09-10
forum: General Help
---

### Post by Matthew2D on 2012-09-10
Im 13 and in Tech Club at my school. My school provides us with laptops. Would it be best to use virtual box to install ubuntu or the windows web installer?

---

### Post by overdrank on 2012-09-10
Hi and welcome. Since you do not own the equipment then I would say you would have to check with the school to see if you could install Ubuntu.

---

### Post by newb85 on 2012-09-10
Definitely find out your school's policy for adding software.

The Wubi Installer will give a separate boot option for Ubuntu at startup.

VirtualBox, on the other hand, would be just like running a program on Windows.  (A very large and powerful program, mind you...)

---

### Post by Stonecold1995 on 2012-09-11
I'd go with the WUBI installer.  It's as easy to install as VirtualBox, and provides much greater speeds.  However to boot into Ubuntu you'll have to reboot each time, same with getting back onto Windows.  VirtualBox on the other hand lets you run Ubuntu IN Windows, so both at once.  If you're fine with rebooting each time to switch OSes I'd strongly suggest WUBI.

Make sure you're allowed to do that on your computer, because it's probably owned by the school.  If they allow you to install another OS then go for it!  If not, you may be able to get away with installing it in VirtualBox if you are allowed to at least install programs (ask your school first of course).

---

### Post by codemaniac on 2012-09-11
> **Matthew2D said:**
> Im 13 and in Tech Club at my school. My school provides us with laptops. Would it be best to use virtual box to install ubuntu or the windows web installer?

Hello and welcome to the forums and Ubuntu :) ,

You should try out the live cd first to see if your hardware is comfortable with it .

---

### Post by newb85 on 2012-09-11
Actually, if you want a separate boot option for Ubuntu, you should *not* use the Wubi installer, as it creates a sub-optimal situation, where your Ubuntu install is a slave to your Windows install.

If you boot from a LiveCD, the installer is extremely easy to use.

Moreover, Wubi was designed for testing purposes, and Wubi originator Agostino Russo never intended it for long-term installations.  See [this article]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/").

---

### Post by mastablasta on 2012-09-11
> **newb85 said:**
> The Wubi Installer will create a separate partition for Ubuntu.

wubi will create virtual disk inside windows. 
 
Virtual box is least intrusive to the OS. it is also very easy: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by tienlbhoc on 2012-09-11
If you are newbie, using virtualbox to try

---

### Post by newb85 on 2012-09-11
> **mastablasta said:**
> wubi will create virtual disk inside windows. 
 
Virtual box is least intrusive to the OS. it is also very easy: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Wow, I really need to do a better job of checking my info...

---

### Post by Moif_Murphy on 2012-09-11
This is just down to personal taste but I'd go with VMWare Player and the Ubuntu 12.04 images.

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
[http://vmplanet.net/2012/07/ubuntu-12-04-lts/](http://vmplanet.net/2012/07/ubuntu-12-04-lts/)

VMWare Player as a portable app:

[http://www.heroturko.me/softwares/flash-tools/1026325-vmware-player-314-build-385536.html](http://www.heroturko.me/softwares/flash-tools/1026325-vmware-player-314-build-385536.html)

---

### Post by Matthew2D on 2012-09-11
I am aloud to. Im one of three students in the whole school that knows the admin password.

---

### Post by Megaptera on 2012-09-11
> **Matthew2D said:**
> I am aloud to. Im one of three students in the whole school that knows the admin password.

Does that mean you're *supposed* to know it though - have you got specific permission for this project? Just asking 'cos better safe than sorry.

If poss then my vote goes for a full dual boot.

---

