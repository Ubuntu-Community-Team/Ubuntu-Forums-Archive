---
title: "Remote desktop when not logged in"
date: 2011-02-28
forum: General Help
---

### Post by tidefan on 2011-02-28
I have searched some posts and did not see the problem i am having. I have built a 10.10 desktop. I need to place it in a building and will not log into it locally unless i absolutely have to. I want to be able to connect to the box and get a desktop if needed. I have been able to do that, but only when i have a user logged into the box. If i log out of the box, my VNC client will not connect. I am able to connect via SSH, but that is it. If i ever need to reboot the box for any reason, i do not want to have to drive across town to log back into the box locally. I have a vnc server installed and Open ssh. can someone help me to understand how i can connect to that box and get a desktop? thanks in advance.

---

### Post by spiky001 on 2011-02-28
I have mine set to login automatic if this helps

---

### Post by tidefan on 2011-02-28
> **spiky001 said:**
> I have mine set to login automatic if this helps

i have thought about this. But i have a network scanner on here that i dont want anyone connecting to. And since the box will be in some shared space, i would rather it not be logged on from boot.

---

### Post by pricetech on 2011-02-28
Make sure SSH Server is installed and download and install NX from nomachine dot com.  You'll need the Client, Node, Server for Linux.

They have a Windows client too in case you need one.

Works for me both locally and over the net.

---

### Post by tidefan on 2011-03-01
Thanks. I tried NX and did not have any luck with it. Very confusing and could not get it to work. I ended up installing XRDP and everything is working fine with it now. Thanks again for the help.

---

