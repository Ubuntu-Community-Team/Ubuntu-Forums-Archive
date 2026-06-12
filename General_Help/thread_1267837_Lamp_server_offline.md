---
title: "Lamp server offline"
date: 2009-09-16
forum: General Help
---

### Post by anupam sadhukhan on 2009-09-16
How to install LAMP server offline in ubuntu 9.04?
the command used is $sudo tasksel install lamp-server
but $sudo apt-get install lamp-server   can't find the packages.
how to get the links of the packages so that I can download them from other computer?

---

### Post by grizzler on 2009-09-16
According to the file **/usr/share/tasksel/ubuntu-tasks.desc** the LAMP server meta package consists of the packages **apache2** and **mysql-server**.

---

### Post by ChumleyEX on 2009-09-16
Couldn't you just download the server version and reinstall/upgrade with the LAMP option?

---

### Post by mac9416 on 2009-09-17
> how to get the links of the packages so that I can download them from other computer?
Hey, there's an even better way. You can use [Keryx]("http://keryxproject.org/") to get both apache2 and mysql-server (plus any other software you want to install offline). Keryx will download all the necessary dependencies onto your flash drive from your favorite Net-connected computer, then you can take them back to your new offline server and install them with "dpkg -i <filename>".

Another option would be to use [Ubuntu Shipit]("https://shipit.ubuntu.com/"). You can request a free Ubuntu Server Edition CD, which will come with LAMP (and much more) pre-installed.

I have an offline Ubuntu server myself. I have a lot of fun messing with it. I installed Server Edition from a CD I got with Shipit, and I've used Keryx to install lots of goodies. Together, Shipit and Keryx make life much easier for offline users.

Good luck
-mac

---

### Post by EXCiD3 on 2009-09-18
If it's a server you will be using locally, you could probably just use XAMPP easiest.

---

