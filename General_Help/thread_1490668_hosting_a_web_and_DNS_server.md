---
title: "hosting a web and DNS server?"
date: 2010-05-22
forum: General Help
---

### Post by spankermonkey on 2010-05-22
Hello, I'm on Ubuntu 10.04 and I've recently been researching into the idea of hosting my own website and my own DNS server so I don't have to buy one lol. Anyways, I'm new to web hosting and was wondering if I does to I have to register my domain name on the whois database or something? Like tell them who owns the domain if I'm hosting the web and DNS server myself or do I have to tell my ISP or something, or do I not have to do any of that and just go on my merry way with my DNS and web server? Any help?, please?

Thankyou.
-Spankermonkey

---

### Post by bodhi.zazen on 2010-05-22
Yes you need to purchase a domain (fivebean, godaddy, etc). I would not run a DNS server, no real need.

---

### Post by bodhi.zazen on 2010-05-22
Or you can use one of the free dns services, such as dyndns

---

### Post by bacardiandwatermelon on 2010-05-22
> **bodhi.zazen said:**
> Or you can use one of the free dns services, such as dyndns

Ah you bet me to this...

---

### Post by Joe of loath on 2010-05-22
I'm using dyndns, it's great! I've got a web, FTP and SSH server all running from behind my router, and they all work perfectly.

---

### Post by bodhi.zazen on 2010-05-22
> **Joe of loath said:**
> I'm using dyndns, it's great! I've got a web, FTP and SSH server all running from behind my router, and they all work perfectly.

Yep, works great.

You are not really "behind" your router if you forwarded your ports , so make sure you secured ssh and ftp. 

You should probably either configure iptables or install fail2ban.

---

### Post by Joe of loath on 2010-05-22
> **bodhi.zazen said:**
> Yep, works great.

You are not really "behind" your router if you forwarded your ports , so make sure you secured ssh and ftp. 

You should probably either configure iptables or install fail2ban.

Yeah, I'm keeping an eye on the activity while I sort everything out. My passwords are strong though, so I'll probably be OK for the short uptimes while I'm setting up.

---

