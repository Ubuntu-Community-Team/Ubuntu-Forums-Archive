---
title: "Hotel Internet on Ubuntu"
date: 2011-11-12
forum: General Help
---

### Post by OOzypal on 2011-11-12
Hello,

When I travel and use the hotel internet, I always get a username and password to enter on their website to browse. 

Sometime is not convenient as some utilities that not go through the can not connect to the internet.

Is there a way to enter this username and password directly to Ubuntu to serve the net?

Did I explained correctly.:)

Thank you

---

### Post by ElGaton on 2011-11-12
Unfortunately I don't think there's a "direct" way, but you could always open your Web browser, open any site (if you are not authenticated the hotel access point should then redirect you to the authentication page) and input the username and password. The connection should then work (even for third-party applications) until you disconnect.

---

### Post by Rubi1200 on 2011-11-12
I also recommend using the firewall in these situations.

If you are comfortable with the command line you can use ufw and if not there is gufw:
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

