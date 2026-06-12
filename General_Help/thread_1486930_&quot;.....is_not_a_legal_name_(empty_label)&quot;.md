---
title: "&quot;.....is not a legal name (empty label)&quot;"
date: 2010-05-18
forum: General Help
---

### Post by Cotopaxi on 2010-05-18
when I type in terminal:

> host $pool.ntp.org

I get this answer:

> .pool.ntp.org' is not a legal name (empty label)

I am trying to make the system clock synchronize automatically with the ntp server.

Can anyone give me a hand?

Thanks!

---

### Post by WorMzy on 2010-05-18
host returns an/a sequence of IP address(es), or, if a IP address is passed, returns a domain name.

You're getting an error because you're trying to pass the variable "$pool" followed by ".ntp.org"

```
host pool.ntp.org
``` will return
```
pool.ntp.org has address 82.143.255.54
pool.ntp.org has address 87.108.20.69
pool.ntp.org has address 83.98.201.133
```

---

### Post by Cotopaxi on 2010-05-18
Thanks for your reply!

Leaving the "?" out solved it.

Now I have another question:

> ntptrace pool.ntp.org

gives me the following output:

> ntp01.cdmon.com: timed out, nothing received
***Request timed out 

Can you help me on this one?

Thanks again! :popcorn:

---

### Post by WorMzy on 2010-05-18
There must be a problem with your internet connection, it works fine for me:

```
pool.ntp.org: stratum 1, offset -0.001505, synch distance 0.003896, refid 'DCFi'
```

Try it again, perhaps there was a temporary problem. If you're still having problems, try reinstalling ntp:
```
sudo apt-get install ntp --reinstall
```

---

### Post by Cotopaxi on 2010-05-18
WorMzy,

Again thanks for your reply!

In my case the problem persists. I will check tomorrow, if it is a firewall issue (Guarddog).

Again, thanks for your help!:popcorn:

---

### Post by srs5694 on 2010-05-18
The pool.ntp.org hostname, and others like it, resolve to a variety of servers in a round-robin fashion. Thus, there's a good chance that Cotopaxi and WorMzy were using different servers, despite the fact that they were using the same hostname. FWIW, I found that ntp01.cdmon.com (the hostname referred to in Cotopaxi's error message) resolves to 212.36.75.245. When I tried to query it using ntpq, I got a timeout error. When I checked pool.ntp.org. I got different IP addresses, none of which was 212.36.75.245. I tried using ntpq four times. Three attempts succeeded, although one of those showed that the server clearly had no external time source. Two other attempts connected to what were clearly different servers, each with what seemed like reasonable upstream servers. Overall, not a very promising set of results.

Thus, the solution in this case is just to wait, or at most, restart the NTP server on the local system. Sooner or later, the bad server will drop off the list and everything will start working.

Another option is to locate a specific NTP server that's known to be good. Your ISP might offer one, for instance.

---

