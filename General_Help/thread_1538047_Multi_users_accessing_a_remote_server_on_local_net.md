---
title: "Multi users accessing a remote server on local network"
date: 2010-07-24
forum: General Help
---

### Post by UranUtan on 2010-07-24
Hi,

I would like to experiment a "green" idea of virtual desktop where multiple users are served by a single powerful machine.   

I have a server running 24/7. The monitor of this machine is turned off most of the time and the OS is on the login screen.
 
Other users, in the same local network, use less powerful machines, which could be a thin client or an old Pentium 3 machine. They access their accounts remotely and work with the GUI as if they were sitting in front of the server. Each user sees their own desktop (different themes, screen resolution, etc.). And of course it can happen that several users could log in at the same time.

The usage is modest: mostly web browsing and the usual default applications (office, wine, gimp, etc.). In particular no games or any demanding applications. The users want to use their desktop in graphical mode only.

**Question:** How do we call this way of using a server? Is it possible with Ubuntu? And how to implement it?


Thank you in advance for any help.

---

### Post by uRock on 2010-07-24
What you want is doable, but it will take some time and patience to get it going. To do this with each system running its GUI off of the server you will have to set up the systems for a network boot. Check out these links;

[http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/](http://ubuntu-tutorials.com/2007/10/11/how-to-configure-pxe-network-booting-on-ubuntu-for-network-based-installations/)

[http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

[http://myy.helia.fi/~karte/ubuntu_pxe.html](http://myy.helia.fi/~karte/ubuntu_pxe.html)

---

### Post by UranUtan on 2010-07-24
Hi uRock,

Wow this sounds complicate. Will try to read further. Thanks.


Found **Useful Multiplier** while researching on the subject:
[http://userful.com/products/userful-multiplier/how-its-done](http://userful.com/products/userful-multiplier/how-its-done)

This is a solution using a single computer to drive multiple monitor-keyboard-mouse. Not exactly what I was looking for but nevertheless a very interesting solution.

---

### Post by uRock on 2010-07-24
I tried to set up the PXE boot before and was deterred by the amount of work, but with time and patience it would be a good setup.

Cheers & Beers,
uRock

---

