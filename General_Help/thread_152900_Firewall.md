---
title: "Firewall?"
date: 2006-03-30
forum: General Help
---

### Post by captainjy on 2006-03-30
Man, I am really new to Linux and am having some trouble.  I am trying to get this box configured as a backup DNS server and I have managed to get DNS installed, but I am trying to setup a client to use this Ubuntu box for DNS, but I cannot ping it.  From the Ubuntu server, I can go to the Internet and access other servers on the LAN.  Is there some sort of firewall configured on this server?

---

### Post by DjKritical on 2006-03-30
There is a firewall built into linux called iptables

By default it should allow everything,

Install a package called "Firestarter" if you want to configure the firewall easily...


If you can't ping the machine then it's more likely your network settings which are incorrect,

Type in ifconfig which will show you your network settings... maybe post them in here?

Also you can edit your network settings by typing this...

sudo gedit /etc/network/interfaces

you can actiuvate the changes by typing

sudo invoke-rc.d networking restart

Good luck :-D

---

### Post by captainjy on 2006-03-31
Thanks, I will check that out.  Appreciate the suggestion.

---

