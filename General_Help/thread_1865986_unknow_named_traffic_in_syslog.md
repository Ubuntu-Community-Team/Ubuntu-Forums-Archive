---
title: "unknow named traffic in syslog"
date: 2011-10-20
forum: General Help
---

### Post by mkhurram92 on 2011-10-20
There are alot of logs just like below in syslog in Ubuntu 10.04

Oct 21 02:36:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:36:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:36:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:37:09 Gateway-Server named[1248]: lame server resolving 'tep.xylocomod.com.com.sa' (in 'com.com.sa'?): 64.38.13.30#53
Oct 21 02:38:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:38:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:38:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:38:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:41:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:41:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:41:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:41:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:41:25 Gateway-Server named[1248]: lame server resolving 'tep.xylocomods.com.com.sa' (in 'com.com.sa'?): 64.38.13.29#53
Oct 21 02:41:25 Gateway-Server named[1248]: lame server resolving 'tep.xylocomods.com.com.sa' (in 'com.com.sa'?): 64.38.13.30#53
Oct 21 02:43:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:43:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:43:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:43:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:44:40 Gateway-Server named[1248]: lame server resolving 'tep.xylocomod.com.com.sa' (in 'com.com.sa'?): 64.38.13.29#53
Oct 21 02:46:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:46:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:46:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:46:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:48:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:48:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:48:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:48:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:49:39 Gateway-Server named[1248]: lame server resolving 'tep.xylocomod.com.com.sa' (in 'com.com.sa'?): 64.38.13.30#53
Oct 21 02:51:12 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:51:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:51:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:51:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:53:42 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:53:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:53:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:53:43 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:53:54 Gateway-Server named[1248]: lame server resolving 'tep.xylocomods.com.com.sa' (in 'com.com.sa'?): 64.38.13.29#53
Oct 21 02:53:54 Gateway-Server named[1248]: lame server resolving 'tep.xylocomods.com.com.sa' (in 'com.com.sa'?): 64.38.13.30#53
Oct 21 02:56:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.84.25#53
Oct 21 02:56:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 67.208.74.19#53
Oct 21 02:56:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.26.176.28#53
Oct 21 02:56:13 Gateway-Server named[1248]: error (unexpected RCODE REFUSED) resolving 'tep.xylocomods.com/A/IN': 69.93.94.154#53
Oct 21 02:57:10 Gateway-Server named[1248]: lame server resolving 'tep.xylocomod.com.com.sa' (in 'com.com.sa'?): 64.38.13.29#53

What type of these logs are + what i have to do to troubleshoot this error ????
Please Guide

---

### Post by pizza-is-good on 2011-10-20
You may want to remove the [SOLVED] tag to your title, the people who can help won't come, and those who are interested in the solution but have no idea how to solve it (like me), will be disappointed :)

---

### Post by mkhurram92 on 2011-10-20
hello pizza-is-good,
actually it is 3 AM in my country. Feeling sleep. 
By the way thanks for your correction :P

---

### Post by dcstar on 2011-10-21
> **mkhurram92 said:**
> There are alot of logs just like below in syslog in Ubuntu 10.04
.........
What type of these logs are + what i have to do to troubleshoot this error ????
Please Guide

They look like errors from your DNS server, check the configuration of the forwarders.

---

### Post by mkhurram92 on 2011-10-22
> **dcstar said:**
> They look like errors from your DNS server, check the configuration of the forwarders.
Forwarder has just DNS Records of ISP and nothing more than this.

---

### Post by dcstar on 2011-10-22
> **mkhurram92 said:**
> Forwarder has just DNS Records of ISP and nothing more than this.

Then you have some bogus configuration issue or program on your system:

```
Oct 21 02:57:10 Gateway-Server named[1248]: lame server resolving 'tep.xylocomod.**com.com**.sa' (in 'com.com.sa'?): 64.38.13.29#53
```

The problem is obvious.

---

### Post by mkhurram92 on 2011-10-22
> **dcstar said:**
> Then you have some bogus configuration issue or program on your system:

```
Oct 21 02:57:10 Gateway-Server named[1248]: lame server resolving 'tep.xylocomod.**com.com**.sa' (in 'com.com.sa'?): 64.38.13.29#53
```

The problem is obvious.

Well this system is just forwarding queries to the ISP Name Servers. Nothing More than this. For internal query resolve i have internal DNS installed on Windows Server 2008. So how i can trace the problem ???

---

### Post by dcstar on 2011-10-22
> **mkhurram92 said:**
> Well this system is just forwarding queries to the ISP Name Servers. Nothing More than this. For internal query resolve i have internal DNS installed on Windows Server 2008. So how i can trace the problem ???

Put in a packet sniffer and find out what device on your network is making those bogus DNS requests.

---

