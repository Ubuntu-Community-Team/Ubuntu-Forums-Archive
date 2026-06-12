---
title: "Accessing a website that has 127.0.0.1 set as its IP"
date: 2011-01-17
forum: General Help
---

### Post by lazypeterson on 2011-01-17
Every time I try and visit this website I get brought to my default localhost page. I've pinged the website and my terminal reads:

64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.019 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.027 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.030 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.026 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.028 ms

I've also thrown the domain into [http://www.opendns.com/support/cache/](http://www.opendns.com/support/cache/) to make sure it wasn't something up locally... again it came up as 127.0.0.1. Is there any way I'd be able to access this site?

---

### Post by psusi on 2011-01-17
> **lazypeterson said:**
> 
I've also thrown the domain into [http://www.opendns.com/support/cache/](http://www.opendns.com/support/cache/) to make sure it wasn't something up locally... again it came up as 127.0.0.1. Is there any way I'd be able to access this site?

There is no such site.

---

### Post by v1nny on 2011-01-17
> **lazypeterson said:**
> 
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.019 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.027 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.030 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.026 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.028 ms


127.0.0.1 is the IP address for the loopback device. That means that you are accessing the computer you type that address into directly. That is also why you have ping times so low. Even computers connected directly via cat5 ethernet will have ping times >1ms.

---

### Post by lazypeterson on 2011-01-17
Any possibilities on why this is happening, exactly?

---

### Post by v1nny on 2011-01-17
> **lazypeterson said:**
> Any possibilities on why this is happening, exactly?

Most likely whoever owns/setup the dyndns domain misconfigured their client to use the loopback interface instead of the external interfaces. (On Ubuntu, you can use the command "ifconfig -a" to show all the available interfaces).

---

### Post by lazypeterson on 2011-01-17
> **v1nny said:**
> Most likely whoever owns/setup the dyndns domain misconfigured their client to use the loopback interface instead of the external interfaces. (On Ubuntu, you can use the command "ifconfig -a" to show all the available interfaces).

Ah thanks. Embarrassingly, it turns out the site was shut down as of today. I thought it was a personal problem because my local files were all showing up. Thank you all for your help nonetheless.

---

