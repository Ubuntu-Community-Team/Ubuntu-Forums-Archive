---
title: "DDClient - How do you configure?"
date: 2009-08-03
forum: General Help
---

### Post by siabost on 2009-08-03
Hi,

Not sure where to post this so here it is!

I have bought a domain name and I would like to run a website from a computer running on my home network.

Because I have a dynamic network ip address (my router/isp sort out a new one every now and then) I've opened an account with [www.zoneedit.com](www.zoneedit.com). After loading DDClient via Synaptic that should've been it(?).

But I may not have filled in the correct info when DDClient was installing as it seems to be trying to update my exterior ip with my local one - which obviously wont work.

Does anyone know how to set up DDClient correctly?

Many thanks.

---

### Post by nucleuskore on 2009-09-16
[http://ubuntuforums.org/showthread.php?t=1264710](http://ubuntuforums.org/showthread.php?t=1264710)

---

### Post by PapaGoose on 2009-09-19
That won't work for zoneedit, those config instructions are for dyndns. What you need to do is install ddclient with apt-get however you like, and then change your /etc/ddclient.conf file to:

```
pid=/var/run/ddclient.pid
protocol=zoneedit1
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=dynamic.zoneedit.com
login=<zoneedit username>
password=<zoneedit password>
your.domain.com
ssl=yes
daemon=300
```

And then don't forget to restart ddclient with

```
sudo /etc/init.d/ddclient restart
```

This setup is working well for my zoneedit account :)

---

### Post by siabost on 2009-09-21
Thanks PapaGoose,

It seems to be working.

One note for anyone else doing this - when you make a change to the config file give it a little time before assuming it is/isn't working. I got myself into a right muddle due to impatience!

All ok now, though.

Ta much. :)

---

