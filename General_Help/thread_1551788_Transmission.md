---
title: "Transmission"
date: 2010-08-12
forum: General Help
---

### Post by Dxlnc on 2010-08-12
Hello people!

As you obviously will realize, I am quite new to Linux, and while I so far like it, some things kill me and my researching skills, so I am forced to ask for help.

It seems that no matter what ports I choose in Transmission, they are always closed, anyone have the faintest idea why? Thank you:-)

- Dxlnc

---

### Post by earthpigg on 2010-08-12
you said you where getting 400kb/s using transmission in the [other thread]("http://ubuntuforums.org/showthread.php?t=1551757"), indicating that it's working. what changed?

---

### Post by jerenept on 2010-08-12
If Transmission works fine, then I wouldn't worry about it too much.

Selecting an automatic port using uPnP is probably the best idea, however, rather than manually choosing a port.

---

### Post by Dxlnc on 2010-10-07
I still got data, but still slowly, the ports were always still closed:-)

---

### Post by mcduck on 2010-10-07
> **Dxlnc said:**
> I still got data, but still slowly, the ports were always still closed:-)

What kind of network setup are you using?

Unless you have yourself set up a firewall, there's nothing closing any ports in Ubuntu itself.

If you are using a router you should check it's settings, and either enable uPnP in both the router & Transmission, or use port redirection in the router to direct traffic on the port you selected in Transmission to the Ubuntu machine.

---

