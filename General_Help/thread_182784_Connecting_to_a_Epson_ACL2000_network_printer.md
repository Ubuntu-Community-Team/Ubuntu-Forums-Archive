---
title: "Connecting to a Epson ACL2000 network printer"
date: 2006-05-26
forum: General Help
---

### Post by Morientes on 2006-05-26
Hi!

I have a Windows machine that shares my network printer - this is the only way that I can make Ubuntu reach it. The printer is an Epson AcuLaser 2000. My problem with this way of setting it up is that now my windows machine has to be turned on for me to print from linux.

Since my printer has an IP-adress I should be able to connect to it directly from linux but my question is how do I do this?

Thanks in advance!

---

### Post by johnc4510 on 2006-05-26
This web site might help:
[http://www.linuxprinting.org/cups-doc.html](http://www.linuxprinting.org/cups-doc.html)

---

### Post by Morientes on 2006-05-28
Hm I cant get it to work. I have added the printer and I am quite sure I used the correct IPP adress since its what my printer says. However absolutely nothing happens when I try to print! It just says "Unknown printer error (other error)!".
I have added this line to my locations in the cupsd.conf: Allow From 192.168.1.0/24

There is absolutely no contact to the printer however!

Any ideas?

---

### Post by Morientes on 2006-05-29
Bump!

Please...no ideas?

---

### Post by Morientes on 2006-06-04
bump again!

---

### Post by Morientes on 2006-06-05
I have now found out that if I select Windows network when setting up the printer it can see the printer. It shows a network named EPSON. Now, when I select this network it asks for login information. I have no idea what that might be? Could there be some default username/password for an Epson ACL2000 ?

---

