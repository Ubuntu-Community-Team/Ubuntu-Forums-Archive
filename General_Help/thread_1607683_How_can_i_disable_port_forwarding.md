---
title: "How can i disable port forwarding?"
date: 2010-10-28
forum: General Help
---

### Post by Abol_fa on 2010-10-28
i have already changed the sshd_config file but anyone who logs in can access to the internet what should i do?:confused:

---

### Post by spikoley on 2010-10-28
Port forwarding is set up in your router.  Find your router on this [site]("http://portforward.com/") for directions on where to disable it.

---

### Post by Abol_fa on 2010-10-28
> **spikoley said:**
> Port forwarding is set up in your router.  Find your router on this [site]("http://portforward.com/") for directions on where to disable it.
tnx but i'm trying to coonect to ssh by localhost 
do i still need to change routers setting?

---

### Post by linux-hack on 2010-10-28
[http://www.linux-france.org/prj/edu/archinet/systeme/ch13s04.html](http://www.linux-france.org/prj/edu/archinet/systeme/ch13s04.html)

turn it off like this :

```
echo "0" > /proc/sys/net/ipv4/ip_forward
```

---

### Post by Abol_fa on 2010-10-28
> **linux-hack said:**
> [http://www.linux-france.org/prj/edu/archinet/systeme/ch13s04.html](http://www.linux-france.org/prj/edu/archinet/systeme/ch13s04.html)

turn it off like this :

```
echo "0" > /proc/sys/net/ipv4/ip_forward
```
thank u too :D still another but..:D
how do i enable it? 
The link that you gave me is in france:confused::(

---

### Post by linux-hack on 2010-10-29
[http://wiki.freaks-unidos.net/ssh-port-forwarding](http://wiki.freaks-unidos.net/ssh-port-forwarding)
[http://magazine.redhat.com/2007/11/06/ssh-port-forwarding/](http://magazine.redhat.com/2007/11/06/ssh-port-forwarding/)
and if you want to enable it you just do this :

```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

---

