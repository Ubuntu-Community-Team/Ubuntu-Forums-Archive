---
title: "Need help running a .rdp file (Windows remote desktop connection)"
date: 2011-01-06
forum: General Help
---

### Post by 0949er on 2011-01-06
Hey guys, I have come across a problem while using Linux during my college carreer.

We have the option of connection to our campus computers via a Windows Remote Desktop connection that give us access to programs such as AutoCAD, Adobe Acrobat Pro, Microsoft Office, etc.

The problem is that you connect to this system via clicking a link on our website, which is  a ".rdp" file that would open up windows remote desktop connection, and connect you.

Do I have any solutions to running .rdp files on linux? What about through Wine? how would I do this? Any help would be greatly appreciated, I need to access these programs from home, and do not want to dual boot windows to do it *yuck*

Thanks guys.

*update* I have tried installing "remote desktop" on windows, but I am unable due to not having "TCP/IP Settings" installed. That means im sure a infinite loop of windows dependencies.

---

### Post by perspectoff on 2011-01-06
RDP is built into the Remote Desktop Connection of Ubuntu. It doesn't need anything special. Have you actually tried it yet?

---

### Post by 0949er on 2011-01-07
Remote desktop connection does not know how to handle the "*.rdp" files I am downloading.

---

### Post by Tankety on 2011-09-16
You can use Tsclient to open the RDP files by default through Firefox.  Or you could open the file with gedit and copy/paste the ip: port into rdesktop using RDP.  In Tsclient, you may have to set it to use RDPv5.

---

