---
title: "How to find what DNS server is handed out with DHCP"
date: 2010-06-27
forum: General Help
---

### Post by eric_1982 on 2010-06-27
This may be a dumb question but in windows you can do an Ipconfig /all and see all your network information such as DNS servers assigned by my DHCP server. How can I see this same information in ubuntu?

If I do a ifconfig I see real basic information but not the DNS or the gateway information.

---

### Post by cariboo on 2010-06-28
Right the network icon in the top panel and select Connection information.

---

### Post by Spr0k3t on 2010-06-28
From the terminal you can use [FONT="Lucida Console"]nslookup host[/FONT] or even [FONT="Lucida Console"]dig[/FONT].  I'm sure there are other commands out there which would do the trick for showing your DHCP handed DNS list.

---

### Post by endotherm on 2010-06-28
I believe that the server address is written to /etc/resolv.conf when you get your dhcp info,
so try
```
cat /etc/resolv.conf
```'cat', just prints the contents of a file, or combines the contents of several files (con**cat**enation).

---

