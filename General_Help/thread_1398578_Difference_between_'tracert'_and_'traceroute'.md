---
title: "Difference between 'tracert' and 'traceroute'"
date: 2010-02-04
forum: General Help
---

### Post by Admiral_Payne on 2010-02-04
Can anyone tell me what the difference between the commands tracert and traceroute is?
I need to run tracert as superuser, while traceroute is no problem in user mode.

Also, it appers like tracert is showing nodes completely different from traceroute:

```
sudo tracert google.nl
traceroute to google.nl (216.239.59.104), 30 hops max, 60 byte packets
 1  192.168.1.254 (192.168.1.254)  1.078 ms  1.699 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * 64.233.174.185 (64.233.174.185)  42.272 ms  46.180 ms
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * gv-in-f104.1e100.net (216.239.59.104)  42.412 ms
```

```
traceroute google.nl
traceroute to google.nl (216.239.59.104), 30 hops max, 60 byte packets
 1  192.168.1.254 (192.168.1.254)  1.130 ms  1.769 ms  2.416 ms
 2  xxxxxxxxxxxxxxxxxxx  41.302 ms  41.509 ms  41.722 ms
 3  core1.ams.net.google.com (195.69.144.247)  42.030 ms  42.247 ms  42.463 ms
 4  209.85.248.93 (209.85.248.93)  42.689 ms  43.357 ms 209.85.248.88 (209.85.248.88)  46.529 ms
 5  209.85.252.29 (209.85.252.29)  71.742 ms 66.249.95.150 (66.249.95.150)  72.072 ms 209.85.252.29 (209.85.252.29)  79.080 ms
 6  64.233.174.185 (64.233.174.185)  79.299 ms  42.850 ms  45.749 ms
 7  216.239.49.114 (216.239.49.114)  55.643 ms 216.239.49.126 (216.239.49.126)  46.703 ms  47.859 ms
 8  gv-in-f104.1e100.net (216.239.59.104)  48.336 ms  51.321 ms  55.263 ms
```


Another thing.. Is it correct to assume that hop 5 and 7 above are loadbalanced nodes?
How should I interpret this result, is the traceroute initiating it's path three times? Otherwise it'd be rather strange as to display other addresses in the same node..

Anyone got experience with these? :)

---

### Post by lloyd_b on 2010-02-04
First off, 'traceroute' and 'tracert' are the *same* program.  What is happening is (I think) that 'traceroute' is using the traditional UDP packets to perform the trace, while running 'tracert' invokes the use of ICMP echo packets (like the Windows program of that name).  Since not all systems respond to the ICMP echo requests, those nodes are showing as "* * *" rather than having valid data as with 'traceroute'.

Note that you should get exactly the same results using 'traceroute -I' as you get with 'tracert'.

As for the second question, here's a bit from the 'traceroute' man page:> [COLOR="Red"]Three probes (by default)  are  sent[/COLOR]  at each  ttl  setting and a line is printed showing the ttl, address of the gateway and round trip time of each probe. The address  can  be  followed  by  additional  information  when requested. [COLOR="Red"]If the probe answers come from different gateways, the address of each responding system will be printed.[/COLOR]So yes, it's sending three probe packets, and telling you when it's getting responses from different routers (as in a load-balanced system).

Lloyd B.

---

### Post by Teunis on 2010-02-05
You don't tell us what you try to find out but another neat utility is mtr, it's quite easy to configure.

---

### Post by Admiral_Payne on 2010-02-05
> **lloyd_b said:**
> First off, 'traceroute' and 'tracert' are the *same* program.  What is happening is (I think) that 'traceroute' is using the traditional UDP packets to perform the trace, while running 'tracert' invokes the use of ICMP echo packets (like the Windows program of that name).  Since not all systems respond to the ICMP echo requests, those nodes are showing as "* * *" rather than having valid data as with 'traceroute'.

Yes, on windows it looks quite similar:

```
Tracing route to google.nl [216.239.59.104]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  192.168.1.254
  2     *        *        *     Request timed out.
  3    40 ms   113 ms   101 ms  core1.ams.net.google.com [195.69.144.247]
  4    24 ms    24 ms    23 ms  209.85.248.88
  5    48 ms    47 ms    47 ms  209.85.252.29
  6    50 ms    47 ms    49 ms  66.249.95.164
  7    49 ms    60 ms    53 ms  216.239.49.126
  8    49 ms    49 ms    49 ms  gv-in-f104.1e100.net [216.239.59.104]

Trace complete.
```

But that would explain the extra access requirement? Because you're sending ICMP packages rather than UDP?

> **Teunis said:**
> You don't tell us what you try to find out but another neat utility is mtr, it's quite easy to configure.

I was trying to do a tracert. Got prompt to install package, so I did. Then I was just wondering why the same package featured these two different commands, for which 'tracert' needed superuser ;)
I'll have a look at mtr, sounds promising.

---

### Post by lloyd_b on 2010-02-05
> But that would explain the extra access requirement? Because you're sending ICMP packages rather than UDP?

Yes - the use of ICMP echo packets requires superuser access.  I'm not entirely sure *why*, but I'm guessing it's a result of such packets, routinely used by the 'ping' utility, being abused on a large scale for a long time.  This is also the reason that many routers simply ignore such packets - by not responding, it becomes more difficult to take down the router with a "ping storm".

Lloyd B.

---

### Post by Admiral_Payne on 2010-02-05
> **lloyd_b said:**
> Yes - the use of ICMP echo packets requires superuser access.  I'm not entirely sure *why*, but I'm guessing it's a result of such packets, routinely used by the 'ping' utility, being abused on a large scale for a long time.
Yes indeed, ICMP packets are used for DDoS ;)

It's quite funny though, that the package comes with traceroute and tracert.. I guess because Windows users are simply used to using tracert :)

---

