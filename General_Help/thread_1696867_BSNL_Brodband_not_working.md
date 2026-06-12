---
title: "BSNL Brodband not working"
date: 2011-02-28
forum: General Help
---

### Post by satish1503 on 2011-02-28
Hi,

I have installed Ubuntu 10.10 with dual boot option on my desktop.
Everything was working fine till yesterday.

Ubuntu used to detect BSNL brodband connection as soon as i turn ON the modem and I could browse the net.

I haven't done any setting for it.

But since yesterday, I can't browse the net even though wired connection id detected by Ubuntu.

I haven't changed any settings.

Can anybody guide me on what went wrong? or what should i check.

Thanks.
Satish

---

### Post by zenwalker on 2011-02-28
Is it an broadband or were you used to do some login to get access to the internet? 

I do have BSNL, its jst connected to Ethernet port from that modem. Its any time on net. So i dont have to do any configuration.

---

### Post by sikander3786 on 2011-02-28
What is the output of these commands please.

```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig
```

---

### Post by satish1503 on 2011-02-28
> **zenwalker said:**
> Is it an broadband or were you used to do some login to get access to the internet? 

I do have BSNL, its jst connected to Ethernet port from that modem. Its any time on net. So i dont have to do any configuration.

Hi,

No need to login. Just turn ON the modem and start browsing.
It was working fine in Ubuntu also... but somehow it is not working now.

Satish

---

### Post by satish1503 on 2011-02-28
> **sikander3786 said:**
> What is the output of these commands please.

```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig
```

Hi Sikander,

I am not at my home. Will post the output of above commands once i am at home.
Thx.

Satish

---

### Post by satish1503 on 2011-03-02
> **satish1503 said:**
> Hi Sikander,

I am not at my home. Will post the output of above commands once i am at home.
Thx.

Satish

Hi,

Problem resolved automatically :)
I don't know how but I switched OFF modem after booting and turned it ON again.

Thanks for your replies.
Satish

---

