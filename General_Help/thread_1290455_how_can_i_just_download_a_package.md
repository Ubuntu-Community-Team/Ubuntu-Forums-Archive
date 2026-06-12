---
title: "how can i just download a package"
date: 2009-10-13
forum: General Help
---

### Post by firsttimeuser on 2009-10-13
I need install libpam-radius-auth on a server without public network connection, so I am trying to download from another server which already installed libpam-radiius-auth and has network connection.

I see there is a -d option for downloading only,but it is not working, can someone tell me why? thanks!

root@backend:/# apt-get  -d install libpam-radius-auth
Reading package lists... Done
Building dependency tree
Reading state information... Done
libpam-radius-auth is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

root@backend:/# apt-get  -d  libpam-radius-auth
E: Invalid operation libpam-radius-auth

---

### Post by fowie on 2009-10-13
look in /var/cache/apt/archives on the computer that you have installed that package on, it should be in there.

---

### Post by firsttimeuser on 2009-10-13
ah, thanks

---

