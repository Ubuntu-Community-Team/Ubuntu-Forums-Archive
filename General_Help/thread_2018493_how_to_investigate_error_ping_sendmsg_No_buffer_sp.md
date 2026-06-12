---
title: "how to investigate error: ping: sendmsg: No buffer space available"
date: 2012-07-06
forum: General Help
---

### Post by masuch on 2012-07-06
Hi,

I have got error within:
```

ping www.google.com

```

ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

Could anybody please help me how to find out what is causing it ?


I have tried to setup 
echo 83886080 > /proc/sys/net/core/wmem_max
with no luck.

this error is NOT appearing on another ubuntu instance on the same computer. I do not want to reinstall current ubuntu instance or clone/rsync another instance over this one.

thank you in advance,
Kind Regards,
Martin

---

### Post by satish_j on 2012-07-20
> **masuch said:**
> Hi,

I have got error within:
```

ping www.google.com

```

ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

Could anybody please help me how to find out what is causing it ?


I have tried to setup 
echo 83886080 > /proc/sys/net/core/wmem_max
with no luck.

this error is NOT appearing on another ubuntu instance on the same computer. I do not want to reinstall current ubuntu instance or clone/rsync another instance over this one.

thank you in advance,
Kind Regards,
Martin

Are you using on-board NIC?Can you post output of
```

lspci | grep -i ethernet

```

---

### Post by masuch on 2012-07-20
> **satish_j said:**
> Are you using on-board NIC?Can you post output of
```

lspci | grep -i ethernet

```

thanks for helping me out.

Yes.
lspci | grep -i ethernet
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
10:00.0 Ethernet controller: Intel Corporation 82583V Gigabit Network Connection

---

### Post by satish_j on 2012-07-23
I am facing similar issue with my on-board LAN,though i have Atheros model.
I have recently disabled the on-board LAN and installed an external Ethernet card in PCI slot.
All is working fine since installing it,iam monitoring the issue and keeping my fingers crossed.will update it..

---

### Post by masuch on 2012-07-25
From time I post it - I have changed configuration for dnsmasq , bind9 , dnscrypt-proxy , network-manager, peer guardian , iptables , create some virtual bridges / changed my home LAN connectivity/structure - from that time - within last couple of days I did not get this massage yet - maybe I had/have some network configuration problem/s ?
But I would like to know what is causing it anyway if it is going to happened again which I believe it will ?

---

### Post by satish_j on 2012-07-27
Same here,i did a lot of tweaking to get it working,but failed.But,i must say that ever since i have switched to external LAN card,the problem has not occurred even once.:)
I suppose the root cause of the problem lies somewhere with On-board LAN.

---

### Post by masuch on 2012-07-28
> **satish_j said:**
> Same here,i did a lot of tweaking to get it working,but failed.But,i must say that ever since i have switched to external LAN card,the problem has not occurred even once.:)
I suppose the root cause of the problem lies somewhere with On-board LAN.

But your problem could be different as I mentioned in the first post that It happened only on one Ubuntu instance (mainly using) but NOT on Ubuntu instance/es which I sometimes run on the same computer - so in my case - it could not be problem within on-board network card - it has to be problem within my configuration.

---

### Post by satish_j on 2012-07-30
> **masuch said:**
> But your problem could be different as I mentioned in the first post that It happened only on one Ubuntu instance (mainly using) but NOT on Ubuntu instance/es which I sometimes run on the same computer - so in my case - it could not be problem within on-board network card - it has to be problem within my configuration.

I guess you are right..Your problem may be different..
Iam using 10.04 & 12.04 on same computer and facing the problem on both.

---

