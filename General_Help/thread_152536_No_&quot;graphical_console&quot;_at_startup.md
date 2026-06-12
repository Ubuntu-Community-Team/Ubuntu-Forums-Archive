---
title: "No &quot;graphical console&quot; at startup"
date: 2006-03-30
forum: General Help
---

### Post by Matthai on 2006-03-30
I have 32 computers with Ubuntu. I did the setup the following way: setup one computer and then clone it to other 31 computers.

The problem is, that computers are not exactly the same. They are two versions of motherboards - actually graphic cards, which are integrated.

Computers are dual boot, and under windows I had to reinstall graphic card in all computers. But under Linux everything works fine, except one thing.

When I boot the computer, sometimes graphical console is not activated. User gets into ordinary black console. Then you shuld press ctrl+alt+F7 and then you can login. X server is working, kdm too, but graphical console is not automatically activated. 

Any help?

---

### Post by feathers on 2006-03-30
Funny, maybe you should just reconfigure X. Type sudo dpkg-reconfigure xserver-xorg on the text console and choose the appropriate settings. Maybe that helps.

---

### Post by Barrakketh on 2006-03-30
I was thinking you should reconfigure KDM.

---

