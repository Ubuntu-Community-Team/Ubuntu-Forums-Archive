---
title: "strange behaviour of router"
date: 2010-03-08
forum: General Help
---

### Post by satty8610 on 2010-03-08
All machines A, B and C discussed in this post are virtual machines(on vmware).

B and C are on separate networks.(B has ip add 172.16.208.130 and C has ip add 172.16.209.128. A had 2 network adapters with ip addresses 172.16.208.1 and 172.16.209.1. 
I "supposedly" set-up A as a Router between B and C , by running the command: 
```
on machine B:  ip route add default via 172.16.208.1 
```
```
on machine C:  ip route add default via 172.16.209.1
```

So, now B was able to ping C.

But what I cannot understand is that even when I shut down the "supposed-router" A , B is still able to ping C. How is that possible? If A is acting as a default gateway that forwards all packets from B to C, then shutting A down should stop B from being able to ping C.

Also, on doing [HTML]tcpdump -i eth0 at A[/HTML] , I am unable to catch any packets(this is while B is pinging C)

Please let me know whats the cause of this, and whether I have set up the router or not?

---

### Post by dcstar on 2010-03-08
> **satty8610 said:**
> 
.........
But what I cannot understand is that even when I shut down the "supposed-router" A , B is still able to ping C. How is that possible? If A is acting as a default gateway that forwards all packets from B to C, then shutting A down should stop B from being able to ping C.

Also, on doing [HTML]tcpdump -i eth0 at A[/HTML] , I am unable to catch any packets(this is while B is pinging C)

Please let me know whats the cause of this, and whether I have set up the router or not?

Basic networking when you have one Ethernet segment:

```
man arp
```

---

### Post by satty8610 on 2010-03-08
Can you explain some more about that

---

