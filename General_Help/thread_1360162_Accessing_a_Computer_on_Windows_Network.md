---
title: "Accessing a Computer on Windows Network"
date: 2009-12-20
forum: General Help
---

### Post by madmax.santana on 2009-12-20
I am connected to a Local Area Network in which each computer has its own static IP. In Windows when I want to open shared folders of any computer on network I open the "run" dialogue box and type in "\\192.168.100.xx" while xx is the IP post script of computer.
How do I open run and do the same in Ubuntu?

---

### Post by PseudoLemon on 2009-12-20
Run in Ubuntu should be alt+f2.

---

### Post by madmax.santana on 2009-12-20
Thanks but what are path standards?
I mean when I type \\192.168.100.149 Windows automatically understands that I mean this computer on the network.
How would I make Ubuntu understand this? I think there is some pre-script like 

> "abc:///192.168.100.149"

while abc is the protocol or something...


Any ideas on that???

---

### Post by madmax.santana on 2009-12-20
Ok I got it...
I opened the network folder in GNOME and opened and accessed an arbitrary PC... Then I checked the path through GNOME address bar and it was

> smb://PC-Name/

So I opened run dialogue and typed 

> smb://192.168.100.149

 and it completely worked.

So I guess the correct way to do it is

Alt+F2 = Run Dialogue
Type:

> smb://PC-Name

or

> smb://xxx.xxx.xxx.xxx

where xxx.xxx.xxx.xxx is the IP address of the computer.

Thanks a lot PsuedoLemon, you gave me a start. :)

---

