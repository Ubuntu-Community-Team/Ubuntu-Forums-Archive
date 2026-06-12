---
title: "pppoeconf"
date: 2006-02-20
forum: General Help
---

### Post by dhelix on 2006-02-20
Hi

I am using Ubuntu 5.10 and I have pppoe connection.
My ISP demands from me to use a service-name to be able to use its services.I am configuring pppoe connection using pppoeconf,it generates a file /etc/ppp/peers/dsl-provider in which i believe i must put an option to describe this service name.Unfortunatly i dont know how and i couldnt find any usefull help about this. 
When using adsl-setup this service name is described in /etc/ppp/pppoe.conf under option "SERVICENAME",unfortunatly adsl-setup,adsl-start and adsl-stop doesnt exists 
Can you help me,pls? 

10x in advance

---

### Post by dhelix on 2006-02-21
i solved it myself.I think it will be good to include pppoe package in the distribution dvd if possible ofc:)

---

### Post by brightview on 2006-02-21
I have the same problem.
Would you share your experience?

---

### Post by dhelix on 2006-02-22
[QUOTE=brightview]I have the same problem.
Would you share your experience?[/QUOTE]


well first u need to install pppoe package

[http://packages.ubuntu.com/breezy/net/pppoe](http://packages.ubuntu.com/breezy/net/pppoe)

then u need to edit /etc/ppp/dsl-provider

there is a line which looks like this:

pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452" you need to add an option -S servicename

pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452 -S yourservicename"

thats all

it works fine for me now :)

---

### Post by riggs_9mmp on 2006-03-12
install how?

sorry, am noob. will bow to master if master helps.

---

### Post by the_billness on 2006-11-08
> **riggs_9mmp said:**
> install how?

Goto: [http://packages.ubuntu.com/breezy/net/pppoe](http://packages.ubuntu.com/breezy/net/pppoe)

Choose your arch (probably i386)

Choose a mirror (I like Indiana University)

Download the package.

Then run the following command: (put the name of the file you just downloaded where <filename> is)
```

sudo dpkg -i <filename>

```

This will install pppoe conf.

---

