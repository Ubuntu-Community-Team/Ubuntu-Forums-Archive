---
title: "Ubuntu client will connect to the network but not the internet"
date: 2010-02-17
forum: General Help
---

### Post by intermentals on 2010-02-17
I have a small network with 2 clients (both ubuntu 9.10) - they both accept dhcp from the server and will both access the samba share however one will not connect to the internet

I'm a bit stumped - any ideas what to try?

Thanks

---

### Post by intermentals on 2010-02-17
ok so after a reboot neither will connect - I think it's something to do with squid because thats the last thing I tried to configure although I have run dpkg --purge squid since

---

### Post by sefs on 2010-02-17
> **intermentals said:**
> ok so after a reboot neither will connect - I think it's something to do with squid because thats the last thing I tried to configure although I have run dpkg --purge squid since

make sure proper dns info is in "/etc/resolv.conf"

---

### Post by intermentals on 2010-02-17
it seems to be and I haven't changed anything in that file since it was working

---

### Post by sefs on 2010-02-17
What is the info in this file?

---

### Post by intermentals on 2010-02-19
I have fixed the problem - the option domain-name and option domain-name-servers line were missing from dhcpd.conf

thanks

---

