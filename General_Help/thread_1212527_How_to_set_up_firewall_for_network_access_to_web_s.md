---
title: "How to set up firewall for network access to web server?"
date: 2009-07-13
forum: General Help
---

### Post by healee on 2009-07-13
I have installed Apache, PHP, MySQL on ubuntu-desktop edition.  I tested the web server on the local computer.  It worked fine.  However, I can't access from another computer on the same network using the hostname or the IP address.  It worked after I disabled the firewall.  I wonder what setting or rules I need to add for such access.

---

### Post by wojox on 2009-07-13
Open port 80 on your firewall.

---

### Post by miwaypet on 2009-07-13
Add the following rule to allow from any machine on local network:

```
sudo ufw allow from 192.168.0.0/16 to any
```

---

### Post by healee on 2009-07-14
> **wojox said:**
> Open port 80 on your firewall.
Thank you!  I had thought of that but I was not sure about the way of going about it.  I did the following and it worked.

sudo ufw allow proto udp to any port 80 from 192.168.0.0/24
sudo ufw allow proto tcp to any port 80 from 192.168.0.0/24

---

### Post by healee on 2009-07-14
> **miwaypet said:**
> Add the following rule to allow from any machine on local network:

```
sudo ufw allow from 192.168.0.0/16 to any
```
Thanks!  I tried your code but it came up with syntax error.  I did as I set out in the earlier post and it worked.

By the way, what does "/16" after 192.168.0.0 stand for?  I used "/24" as I got from an example somewhere.  I haven't worked out what that meant.  I would appreciate if you tell what that meant.  Somehow I missed that in my earlier life.

---

### Post by miwaypet on 2009-07-14
It is called CIDR ing an ip address. In the example 192.168.1.0/16, you have private network address range of up to 16 ip's on your network.

---

### Post by healee on 2009-07-14
> **miwaypet said:**
> It is called CIDR ing an ip address. In the example 192.168.1.0/16, you have private network address range of up to 16 ip's on your network.
Thank you for your great help and explanation!

---

### Post by healee on 2009-07-16
> **miwaypet said:**
> It is called CIDR ing an ip address. In the example 192.168.1.0/16, you have private network address range of up to 16 ip's on your network.
By the way, could you please tell me in which file that the rules go into.  I tried to locate them after adding the rules but I couldn't.  I have looked hard in /etc/ufw/ufw.conf.  I can't quite work out what other files do, after6.rules  after.rules  before6.rules  before.rules  sysctl.conf  ufw.conf.

---

### Post by alphacrucis2 on 2009-07-16
> **healee said:**
> Thank you for your great help and explanation!

Except that the explanation is not correct. The CIDR is a bit mask so /16 actually refers to a class B subnet of 65,534 usable addresses. The example given:

192.168.1.0/16

Means 192.168.0.0 - 192.168.255.255

To specify a subnet of size 16, the correct way of specifying that subnet using CIDR notation is:

192.168.1.0/28

---

