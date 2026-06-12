---
title: "Applications working properly with SUDO only :( UBUNTU Noteboox 10.10 XUBUNTU"
date: 2010-11-22
forum: General Help
---

### Post by adityachs on 2010-11-22
Hi,

I recently installed Ubuntu 10.10 Maverick notebook version on my HP Compaq nc6400
(Intel core2 CPU T5600@1.83GHZ).

Later installed Xfce4. So, I am now on Xubuntu on top of Ubuntu (it seems).

Coming to my problem, even though application working fine normally, Menu is not displayed in most of the applications. Ex: Transmission, GIMP, Mousepad, Pinta, gedit ........ No application shows the file,edit.. menus.

Also file sharing is also not possible in normal mode. When I right click on any folder or file  sharing option is not visible .

[B]But if I run these applications with SUDO the menus are appearing. When I open nautilus with SUDO , I am able to get sharing options in right click.

[/B]I tried the below command as advised in[ thread.php?p=6474144]("http://wwww.ubuntuforums.org/showthread.php?p=6474144")
But it failed :(
[PHP]
~$ sudo chown -hR abcd:abcd /home/abcd
chown: cannot access `/home/abcd/.gvfs': Permission denied
[/PHP]Please advise what to do? Please help.

---

### Post by adityachs on 2010-11-23
:KSBump

---

### Post by adityachs on 2010-12-03
As no one turned to help...I removed Ubuntu and installed Xubuntu...the problem is resolved.

---

