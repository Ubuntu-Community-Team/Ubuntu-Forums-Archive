---
title: "Problem to forward ports to apache web server"
date: 2006-02-07
forum: General Help
---

### Post by pkopko on 2006-02-07
Hello,

I try to setup my web server running to port 10080 because my ISP provider has block port 80. 

My web server working without router WRT54g v5. If I add my router I can not forward port 10080 to my server. 

I tryed two different DDNS dyndns and no-ip. Same situation of both. 

My WRT54g has gateway mode and it is open net connection by using PPPoe. 

Is it problem in hosts configure? Or what I can try? 

Thanks, 
pkopko

---

### Post by slazh on 2006-02-07
There should be a NAT / PAT option on the router if you want to forward ports.
Check your manual how to set it up.

Have you checked if port 10080 isn't used by something else already (just to be sure)?

---

### Post by pkopko on 2006-02-07
I already open that port from router.

How I can check which port is really not used other device?

Do you I need to listen just port 10080 or gateway port 10080?
(Listen 10080 or Listen 192.168.1.1:10080)

Thanks,
pkopko

---

### Post by slazh on 2006-02-07
On your linux pc, you can check with the command 'netstat -a' what ports are open and in what state (listening, open etc).

I don't have the Linksys WRT54g, but on my Vigor there is this administration page where I can check if there are any active NAT sessions.

[http://wrt-wiki.bsr-clan.de/index.php?title=Port_Forwarding#Port_Mapping](http://wrt-wiki.bsr-clan.de/index.php?title=Port_Forwarding#Port_Mapping)

---

