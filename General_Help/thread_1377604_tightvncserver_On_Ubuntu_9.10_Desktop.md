---
title: "tightvncserver On Ubuntu 9.10 Desktop"
date: 2010-01-10
forum: General Help
---

### Post by Zheldon on 2010-01-10
I've been looking and trying to figure it out on my own, but alas I have failed.  Yes I am new to Ubuntu, and Linux in general.

I would like to setup a tightvncserver on my Ubuntu desktop so I can access it from my windows machine.  It would be nice if this worked like it does on a windows machine in that one does not need to be logged into Ubuntu to use tightvnc to access.

If there is already a good tutorial out there let me know and I'll gladly give it a shot.

---

### Post by Socrates1013 on 2010-02-01
From the terminal:

> sudo apt-get install tightvncserver

Once that installs, from the term type:

vncpasswd

set your pw (8 chars max, it will trunc automatically)

and to start the process type

vncserver

I can connect w/ RealVNC viewer for windows, and UltraVNC for windows as well. If you have an issue w/ your keyboard not mapping correctly, go here 

[http://groups.google.com/group/ec2ubuntu/web/running-an-x-desktop-with-vnc-on-ubuntu-7-10-gutsy-on-amazon-ec2](http://groups.google.com/group/ec2ubuntu/web/running-an-x-desktop-with-vnc-on-ubuntu-7-10-gutsy-on-amazon-ec2)

---

### Post by dreq on 2010-03-16
I have the same problem, i did exactly what you said, i can connect and see the desktop and the cursor of ubuntu 9.10. However, i dont see any windows or menus although on the server they get open.

Edit: I have windows 7 trying to connect to ubuntu 9.10 fully updated.

---

