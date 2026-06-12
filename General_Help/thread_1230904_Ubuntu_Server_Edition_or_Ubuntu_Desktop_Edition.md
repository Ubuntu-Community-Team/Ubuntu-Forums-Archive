---
title: "Ubuntu Server Edition or Ubuntu Desktop Edition"
date: 2009-08-03
forum: General Help
---

### Post by henry83 on 2009-08-03
Hi there, I have recently bought a brand new computer and I want to use it for two purposes, first of all to develop software and second to host a web application that will be used in a small company and also visited by some people, not many, because it is about a specific professional area, soil conservation services. And also as SVN repositories source for development. The question is: should I install Ubuntu Server Edition with ubuntu-desktop (or kubuntu-desktop since I'm a kubuntu user) or just intall ubuntu desktop edition (or kubuntu)? What would be my best choice in this dilema? Thanks.

---

### Post by aysiu on 2009-08-03
Wouldn't you just install Ubuntu Server Edition? I don't understand why you would add *ubuntu-desktop* to that if it's going to be a server.

---

### Post by henry83 on 2009-08-03
well, because I would like to use the computer also for programming, I use Eclipse and I need the window system for it...

---

### Post by lykwydchykyn on 2009-08-03
If you *must* have a GUI on the server (and I understand some people must):
 - Don't use the *buntu-desktop packages.  They install all kinds of stuff that has no business on a server.  Instead, install "xorg" and whichever desktop environment.
 - Speaking of which, instead of KDE or GNOME, go for something minimal like icewm, LXDE, openbox, or (at most) XFCE.  Not only will all of those use less resources, but the code base is smaller so there's less chance that your webserver will lock up and crash because (for example) a compiz plugin goes nuts or some Kwin bling says the wrong thing to the video driver.

---

### Post by wojox on 2009-08-03
Check out this site. Real informative:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  :wink:

---

### Post by aysiu on 2009-08-03
A second for xorg and IceWM if you must have a GUI. Better to make it minimal if it has to be there.

---

### Post by henry83 on 2009-08-03
Thanks guys I appreciate your comments. So to summarize you wouldn't recommend a *buntu desktop edition for hosting a web app, is that right?

---

### Post by Hobgoblin on 2009-08-03
Depends how much of the desktop you will need.  

It's probably easier to install the desktop edition then add whatever server bits you need though.

---

### Post by lykwydchykyn on 2009-08-03
> **henry83 said:**
> Thanks guys I appreciate your comments. So to summarize you wouldn't recommend a *buntu desktop edition for hosting a web app, is that right?

Correct.  It can be done, but it is far from ideal; mostly for the reasons I previously stated.

---

