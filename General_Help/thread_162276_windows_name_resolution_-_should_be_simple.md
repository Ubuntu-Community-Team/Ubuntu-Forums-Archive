---
title: "windows name resolution - should be simple"
date: 2006-04-18
forum: General Help
---

### Post by evillawngnome on 2006-04-18
SO, i have a linux development server on a windows domain. I dont want to mess around with domain security on the box, i just want the linux box to tell the domain controller that its on the network. In other words, if im running a webserver on the linux box, i want to be able to go to any machine on our net and point it to [http://linuxdev/](http://linuxdev/) and be done with it. Ive done this before; but i cant figure out how i did it. Links? Tips?

---

### Post by evillawngnome on 2006-04-18
It is simple:

apt-get install samba

Tah-dah!

---

### Post by cgjones on 2006-04-18
Well, the above and configuring /etc/smb.conf
It's pretty simple though. Just make a backup of smb.conf, then open it up and edit away. It's quite well documented, so just make the changes you need and when you are done, run testparm. This will warn you about possible mistakes in the syntax of smb.conf. And here is a link to the Ubuntu docs on Samba. Not exactly for your situation, but I thought it might help some.

[http://help.ubuntu.com/starterguide/C/ch07.html#sect-samba-server](http://help.ubuntu.com/starterguide/C/ch07.html#sect-samba-server)

---

