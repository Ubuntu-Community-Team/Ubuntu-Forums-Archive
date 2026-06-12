---
title: "linux equivalent of ipconfig /release &amp; /renew?"
date: 2006-03-26
forum: General Help
---

### Post by bionnaki on 2006-03-26
I am doing some tests on my cable line and was wondering what the linux equivalent of windows "ipconfig /release" and "ipconfig /renew" is. I know that ifconfig is what you use, but I am unsure how to release and renew.

anyone know?
thanks!

---

### Post by Barrakketh on 2006-03-26
[QUOTE=bionnaki]I am doing some tests on my cable line and was wondering what the linux equivalent of windows "ipconfig /release" and "ipconfig /renew" is. I know that ifconfig is what you use, but I am unsure how to release and renew.

anyone know?
thanks![/QUOTE]
ifup and ifdown perform the same function AFAIK.

---

### Post by paradox242 on 2008-06-25
So ifdown sends a DHCP release message to the DHCP server? This is not the same as just bringing down the interface, and from what I can gather from the man page, though it is never explicitly mentioned, it doesn't do this. 

What you're looking for are the following commands, listed below along with their Windows equivalents:

"sudo dhclient -r" == "ipconfig /release"
"sudo dhclient"    == "ipconfig /renew"

These commands are even better than ipconfig in that they tell you exactly what's happening during the DHCP transaction.

---

