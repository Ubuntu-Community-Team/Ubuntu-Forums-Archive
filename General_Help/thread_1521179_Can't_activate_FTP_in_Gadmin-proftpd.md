---
title: "Can't activate FTP in Gadmin-proftpd"
date: 2010-06-30
forum: General Help
---

### Post by letmekilluplz on 2010-06-30
Whenever I try to click Activate it just sits there for a moment and stays deactivated... anyone have a solution?

no error messages are shown

---

### Post by tommycahir on 2010-10-27
Hi

I am experiencing the same issue using gadmin-proftpd 0.3.8. anybody got any resolutions for this?

---

### Post by Add1cken on 2011-03-22
You need a working nameserver in your resolv.conf:

/etc/resolv.conf

The format of the file is:

nameserver [IP-OF-THE NAMESERVER]

example: in the text file:

> nameserver 62.63.63.10


You may have more then one nameserver. The first nameserver shall be the  IP of the server itself, if you are running BIND DNS Server.

---

