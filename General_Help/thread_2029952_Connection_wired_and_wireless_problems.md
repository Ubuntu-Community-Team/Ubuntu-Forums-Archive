---
title: "Connection wired and wireless problems"
date: 2012-07-20
forum: General Help
---

### Post by maccapacca on 2012-07-20
Hi, 

Purchased a Acer Revo with Ubuntu installed, being a Windows user it's all Dutch to me but I'm going to persevere as it seems like the right piece of software for a HTPC.

Problem is I cannot connect to the internet in anyway shape or form, wifi is working as I'm typing this on the same wifi, LAN is working as I tested again with this laptop, I am using a Sky Sagem standard router but neither wired or wireless are working, the Revo has connected to both :confused:

Any help would be appreciated.

Thanks

MP

---

### Post by pavi_elex on 2012-07-20
Send output of

```

$ ifconfig -a
```

&

```
$ ifconfig -a | grep 'eth'
```

---

### Post by maccapacca on 2012-07-20
> **pavi_elex said:**
> Send output of

```

$ ifconfig -a
```

&

```
$ ifconfig -a | grep 'eth'
```

When I type ifconfig -a | grep response is

eth0 linkencap:ethernet HWaddr 90:fb:a6:e3:fa:af

Back to $ still no connection

---

### Post by pavi_elex on 2012-07-23
May be your problem has been solved till now, I couldn't reply on weekend.
But if you are still in trouble. Try following commands in terminal.
```

$ sudo ifconfig eth0 up
$ sudo dhclient eth0
```

---

