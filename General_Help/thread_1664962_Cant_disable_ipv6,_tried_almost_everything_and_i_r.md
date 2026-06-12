---
title: "Cant disable ipv6, tried almost everything and i run 1pv4"
date: 2011-01-11
forum: General Help
---

### Post by Bazzi313 on 2011-01-11
Hi CANT DISABLE IPV6, TRIED ALMOST EVERYTHING AND I RUN 1PV4 PLEASE HELP, i heard it makes a big difference, ive tried blacklisting, bad_list file, aliases file.

this is what terminal says:
bazzi@Jaafar:~$ ip a | grep inet6
    inet6 ::1/128 scope host 
    inet6 fe80::6ef0:49ff:fe52:edc1/64 scope link 

 A Begginer so thanks for help

---

### Post by uRock on 2011-01-11
No need to disable it, unless it is causing problems. I have seen where it causes problems in some Windows 7 systems, but not in Ubuntu.

Cheers,
uRock

---

### Post by Bazzi313 on 2011-01-11
> **uRock said:**
> No need to disable it, unless it is causing problems. I have seen where it causes problems in some Windows 7 systems, but not in Ubuntu.

Cheers,
uRock

But i want to know why it isnt disabling ? do u have any idea ill take sc of my file ?

---

### Post by bodhi.zazen on 2011-01-11
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

[http://linuxpoison.blogspot.com/2010/10/how-to-disable-ipv6-in-ubuntu-linux.html](http://linuxpoison.blogspot.com/2010/10/how-to-disable-ipv6-in-ubuntu-linux.html)

Disabling ipv6 *usually* does not make a difference, especially these days.

---

