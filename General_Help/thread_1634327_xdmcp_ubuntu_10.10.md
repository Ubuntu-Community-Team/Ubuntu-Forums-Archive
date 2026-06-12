---
title: "xdmcp ubuntu 10.10"
date: 2010-11-30
forum: General Help
---

### Post by mnorgate on 2010-11-30
I need to setup a xdmcp server on ubuntu 10.10 to allow for remote connections. Obviously this cant be done from the login window as with previous versions of Ubuntu. 

Thanks

---

### Post by lpd on 2011-01-02
In short you can wait for Ubuntu 11.04 or... apply a gdm patch.

[I][https://bugs.launchpad.net/gdm/+bug/408417](https://bugs.launchpad.net/gdm/+bug/408417) :
A patched GDM by Tom Ellis works better (read comments at the bottom of this bug report for details).
[https://launchpad.net/~tellis/+archive/customer1/+packages]("https://launchpad.net/%7Etellis/+archive/customer1/+packages")[/I]

Apply the gdm patch. Also make sure to activate XDMCP by:
sudo nano /etc/gdm/custom.conf 

[daemon]
RemoteGreeter=/usr/lib/gdm/gdmlogin

[xdmcp]
Enable=true

---------
Now restart the system. Another thing. Instead of using xnest as client, use xephyr (sudo apt-get install xserver-xephyr) which actually works...
If you'll be using MS Win, download Xming.

xephyr usage example:

Xephyr :12  -query HOSTNAME -fullscreen
Xephyr :12  -query HOSTNAME -grayscale  -screen 1280x1024
Xephyr :12  -query HOSTNAME -screen 800x600 -once
"-once" means that the server is terminated after one session.

See "How to Xephyr" [http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

### Post by rugbeeprop on 2011-01-03
Thanks. It works for me. 

P.S. I use remmina.

Actually, the standard Terminal Server Client that comes standard with Ubuntu works a lot better.

---

### Post by Alejandro-AR on 2011-07-05
I'm setting up Ubuntu 11.04, and this works for me:
> **lpd said:**
> 
[daemon]
RemoteGreeter=/usr/lib/gdm/gdmlogin

[xdmcp]
Enable=true

:KS

Thank you very much!!

---

