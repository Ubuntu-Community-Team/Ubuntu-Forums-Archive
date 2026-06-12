---
title: "Filezilla one way, not the other???"
date: 2012-07-12
forum: General Help
---

### Post by Bucky Ball on 2012-07-12
Hi all,

Hoping someone can help. Using Filezilla between my laptop and desktop, as per usual, but the desktop can't access the laptop. Have switched to 10.04 instead of 10.10 on the laptop so a couple of things were different. Fixed details, still nothing. Triple checked right details. Nothing.

So I decided to ping the laptop. Nothing:

```
bucky@Studio:~$ ping 192.160.0.160
PING 192.160.0.160 (192.160.0.160) 56(84) bytes of data.
```... and that's it. Just stays like that.

The bizarre bit: I can use Filezilla on the laptop to access the desktop just fine, as per normal. 

This is strange. Hoping people have got some ideas (I don't) because really need to get this happening for study. Tnx in advance ... ;)

---

### Post by dino99 on 2012-07-12
looks like you have set a rule to disallow ping : ufw , iptable, hosts ?

be sure to enable ipforward or none your node instances will be able to ping out.


/etc/sysctl.conf
Net ipv4 ip_forward = 1

---

### Post by Bucky Ball on 2012-07-12
No, all good. Pinging the machine now. Late here and I had the wrong IP in there. So now it is just Filezilla. All the details are right but just 'Can't connect to server' etc.

Will change title accordingly ... 

Cheers.

---

### Post by Bucky Ball on 2012-07-12
Killed that quick. Didn't have SSH server installed on the laptop. Installed, worked. Sweet. Solved. ;)

---

