---
title: "Deb program is not appearing under Add/Remove... in Applications menu"
date: 2009-11-12
forum: General Help
---

### Post by Steve Francis on 2009-11-12
I am trying to install an [alarm clock]("http://alarm-clock.pseudoberries.com/") applet.

I have downloaded the debian file from
[https://launchpad.net/~joh/+archive/ppa/+sourcepub/666566/+listing-archive-extra]("https://launchpad.net/%7Ejoh/+archive/ppa/+sourcepub/666566/+listing-archive-extra")   

When I double-click the debian, the file installs and can be seen in the Synaptic Package Manager.

It's not in the Applications menu though and doesn't appear in the Add/Remove list, nor in the list when I right click on Administration and then Edit Menus.

Is there another way of adding a Menu entry for the installed files?


Note 1:

I tried to use the command line as an alternative
sudo apt-get update
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com cebec1b70570c5c6
sudo apt-get install alarm-clock-applet

which had the response

Reading package lists... Done
Building dependency tree       
Reading state information... Done
alarm-clock-applet is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

Note 2:

There is a [similarly-named program]("http://ubuntuforums.org/showthread.php?t=1144722") which is not the one that I am trying to install.

---

### Post by jerrrys on 2009-11-12
right click on your menu in the top panel and then edit menu. look under debian...is it there?

---

### Post by oldos2er on 2009-11-12
Looks like it's a panel applet. Right-click on an empty portion of your panel, click Add to Panel, and you should see the app listed there.

---

### Post by Steve Francis on 2009-11-12
> **jerrrys said:**
> right click on your menu in the top panel and then edit menu. look under debian...is it there?

Unfortunately, nothing was under Debian. Thanks, anyway, for the suggestion.

> **oldos2er said:**
> Looks like it's a panel applet. Right-click on an empty portion of your panel, click Add to Panel, and you should see the app listed there.

That works!  Thank you.

I haven't heard of a panel applet before. What's the difference between that and a program?

---

### Post by oldos2er on 2009-11-12
> **Steve Francis said:**
> I haven't heard of a panel applet before. What's the difference between that and a program?

 A panel applet only runs on Gnome's panel, not as a separate program.

---

