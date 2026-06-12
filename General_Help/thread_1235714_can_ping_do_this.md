---
title: "can ping do this?"
date: 2009-08-09
forum: General Help
---

### Post by abhilashm86 on 2009-08-09
if i want to check a network/host is active i can send packets and do the job.......
```

abhilash@abhilash:~$ ping -c 1 abhilash.co.nr
PING abhilash.co.nr (208.100.40.200) 56(84) bytes of data.

--- abhilash.co.nr ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


```
when i want to check a host via his email id (like [email]abhilashm86@gmail.com[/email]), if he's online , how can this be done??

---

### Post by Monicker on 2009-08-09
That is definitely not a function for the ping command.  There is no way to tell if a user is online by merely knowing their email address.

---

### Post by abhilashm86 on 2009-08-10
> **Monicker said:**
> That is definitely not a function for the ping command.  There is no way to tell if a user is online by merely knowing their email address.

but it will check a website url and get back the information right?? if i ping someone's ip, can i get any information about his system??

---

### Post by vallis on 2009-08-10
You can use nmap to get information about a system if you have the IP but there is no way to get an IP from an email address.

---

