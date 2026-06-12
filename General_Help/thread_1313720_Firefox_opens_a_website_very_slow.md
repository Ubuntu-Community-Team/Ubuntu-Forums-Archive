---
title: "Firefox opens a website very slow"
date: 2009-11-04
forum: General Help
---

### Post by DeMus on 2009-11-04
I installed Jaunty again, after an experiment with Karmic, and the first moment Firefox was very fast. Now, after some days it takes a long time before something is happening when I want to open a page.
I click on a link and nothing happens. I don't see the light on my switch blink, then suddenly it starts. The address shows up in the addressbar, the lights begin to blink and again after some time the page shows up.
Is this a DNS problem? I tried that yesterday when I saw a thread here from somebody who also though he had DNS problems.
I tried this:
```
~$ time host ubuntu.org
ubuntu.org mail is handled by 10 mx2.upc.es.
ubuntu.org mail is handled by 10 mx1.upc.es.

real	0m0.344s
user	0m0.000s
sys	0m0.008s
```

And I tried this:
```
~$ time host bbc.co.uk
bbc.co.uk has address 212.58.224.138
bbc.co.uk mail is handled by 20 cluster1a.eu.messagelabs.com.
bbc.co.uk mail is handled by 10 cluster1.eu.messagelabs.com.

real	0m0.099s
user	0m0.000s
sys	0m0.000s
```

Both show short lookup times. So I  wonder if that is it. What else could it be?
What else can I do to improve Firefox' speed?
The way it is now is not funny anymore.

---

### Post by QIII on 2009-11-04
lovinglinux has a great troubleshooting guide here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

You can try OpenDNS, but that requires actually editing your connection properties, which you may not want to do.

The first thing from his list that I would try is typing about:config in the navigation bar and finding "network.dns.disableIPv6" and setting the value to "True".

---

### Post by DeMus on 2009-11-04
> **QIII said:**
> lovinglinux has a great troubleshooting guide here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

You can try OpenDNS, but that requires actually editing your connection properties, which you may not want to do.

The first thing from his list that I would try is typing about:config in the navigation bar and finding "network.dns.disableIPv6" and setting the value to "True".

Thanks. The disable IPv6 was true already. But I will read through the lovinglinux page when I get home from work. Got to go now.
Thanks again.
If anybody as other ideas please respond.

---

