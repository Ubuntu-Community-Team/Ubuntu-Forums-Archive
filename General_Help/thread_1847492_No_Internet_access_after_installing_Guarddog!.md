---
title: "No Internet access after installing Guarddog!"
date: 2011-09-20
forum: General Help
---

### Post by Richiegs on 2011-09-20
I am using Ubuntu 10.04. I installed **Guarddog** - a firewall program - in my PC. Because it said I was not a superuser, I typed something guarddog in the terminal to get it started. After a while, I was not able to access the Internet.  Even after I removed **Guarddog**, I still can't access the internet. Please help!

---

### Post by dave01945 on 2011-09-20
hello can you try to ping google type the following in the terminal

```
ping -c 4 google.com
```

and then try (google's ip address)

```
ping -c 4 209.85.146.105
```

and tell us the output also can you post the output of 

```
sudo iptables -L
```

---

### Post by Richiegs on 2011-09-20
> **dave01945 said:**
> hello can you try to ping google type the following in the terminal

```
ping -c 4 google.com
``` - unknown host

and then try (google's ip address)

```
ping -c 4 209.85.146.105
```- sendmsg: Operation not permitted

and tell us the output also can you post the output of 

```
sudo iptables -l
``` - it generated a lot of stuff. What exactly are u looking for? Thanks

---

### Post by Richiegs on 2011-09-20
I remembered typing "gksudo guarddog" in the terminal.

---

### Post by iponeverything on 2011-09-20
```
sudo dpkg --purge guarddog

```

might do the trick

---

### Post by Richiegs on 2011-09-20
> **iponeverything said:**
> ```
sudo dpkg --purge guarddog

```

might do the trick

It finally works. Thank you very much. If I want to install a firewall program, which one do you suggest besides UFW?

---

### Post by iponeverything on 2011-09-21
If it is stock install, there is no firewall needed. The reasons this quite simple -

1) Odds are, your machine is on a non-routeable RFC 1918 private address -- and direct access is not possible from Internet at large without some work on your part.

2) The stock install has no listening services that could provide a vector to compromise the machine.

==

If this whole firewall business is just for your own education, work with iptables directly.

---

