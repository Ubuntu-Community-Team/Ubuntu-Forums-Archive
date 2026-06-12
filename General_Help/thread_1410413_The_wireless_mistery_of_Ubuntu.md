---
title: "The wireless mistery of Ubuntu"
date: 2010-02-18
forum: General Help
---

### Post by Lockheed on 2010-02-18
Here's a brain teaser for the daring.

My laptop: 
Atheros WiFi card with ath5k driver, WICD, 9.04 64 bit, kernel 2.6.31.6.

While connecting to any WiFi network with high channel number, say 11, everything is perfectly fine and ping is as follows
```
~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=2.24 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1.60 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=24.8 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=3.56 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=1.57 ms
64 bytes from 192.168.1.254: icmp_seq=6 ttl=64 time=11.4 ms
64 bytes from 192.168.1.254: icmp_seq=7 ttl=64 time=3.44 ms
64 bytes from 192.168.1.254: icmp_seq=8 ttl=64 time=5.28 ms
64 bytes from 192.168.1.254: icmp_seq=9 ttl=64 time=32.1 ms
64 bytes from 192.168.1.254: icmp_seq=10 ttl=64 time=26.8 ms
64 bytes from 192.168.1.254: icmp_seq=11 ttl=64 time=21.1 ms
64 bytes from 192.168.1.254: icmp_seq=12 ttl=64 time=22.5 ms
^C
--- 192.168.1.254 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11014ms
rtt min/avg/max/mdev = 1.574/13.050/32.190/11.085 ms

```


BUT

When connecting to any WiFi network with low channel number, say 1, I am unable to use internet at all and here is my ping to the router standing next to my laptop
```
~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=14.7 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=4544 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=11918 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=13538 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=12654 ms
64 bytes from 192.168.1.254: icmp_seq=6 ttl=64 time=11745 ms
64 bytes from 192.168.1.254: icmp_seq=7 ttl=64 time=10864 ms
64 bytes from 192.168.1.254: icmp_seq=8 ttl=64 time=9918 ms
64 bytes from 192.168.1.254: icmp_seq=9 ttl=64 time=8945 ms
64 bytes from 192.168.1.254: icmp_seq=10 ttl=64 time=8010 ms
64 bytes from 192.168.1.254: icmp_seq=11 ttl=64 time=7057 ms
64 bytes from 192.168.1.254: icmp_seq=12 ttl=64 time=6170 ms
64 bytes from 192.168.1.254: icmp_seq=13 ttl=64 time=3263 ms
64 bytes from 192.168.1.254: icmp_seq=15 ttl=64 time=6.00 ms
64 bytes from 192.168.1.254: icmp_seq=16 ttl=64 time=2.19 ms
64 bytes from 192.168.1.254: icmp_seq=17 ttl=64 time=3.20 ms
64 bytes from 192.168.1.254: icmp_seq=18 ttl=64 time=20.5 ms
64 bytes from 192.168.1.254: icmp_seq=19 ttl=64 time=5.80 ms
64 bytes from 192.168.1.254: icmp_seq=20 ttl=64 time=6.34 ms
64 bytes from 192.168.1.254: icmp_seq=21 ttl=64 time=871 ms
64 bytes from 192.168.1.254: icmp_seq=22 ttl=64 time=11.9 ms
64 bytes from 192.168.1.254: icmp_seq=23 ttl=64 time=5.45 ms
64 bytes from 192.168.1.254: icmp_seq=24 ttl=64 time=1.82 ms
64 bytes from 192.168.1.254: icmp_seq=25 ttl=64 time=6716 ms
64 bytes from 192.168.1.254: icmp_seq=26 ttl=64 time=8722 ms
^C
--- 192.168.1.254 ping statistics ---
36 packets transmitted, 25 received, 30% packet loss, time 41999ms
rtt min/avg/max/mdev = 1.827/5000.841/13538.763/4898.891 ms, pipe 10

```

Just to make it clear, this test was done on the very same network/router, just with different channel number, 1 minute apart. However, results apply to any network I try to connect to.

Why? I talked with WICD developers and they compiled a beta version of WICD for me but installation of it made no difference. They said it might be because of the wifi driver, so I updated to the newest compat-wireless (by the way, how can I check if the newest version I compiled is really in use in my system?) but it made no difference either.

Anyone up for a wild (or maybe not) guess?

---

### Post by Pjotr123 on 2010-02-18
The solution may be simple: possibly there are some routers in the neighbourhood (your neighbours?) who are already using channel 1 on their wireless routers. Then your router signal, if it's at channel 1 as well, will become considerably weaker, because it'll have to "fight" with the signals of the other routers.

In your router, choose only channel 1, 6 or 11, by the way. Only then there's minimal overlap with other routers in the vicinity.

And check if there's a firmware update available for your router, at the website of the manufacturer of your router. Note: only perform a firmware update with a wired connection (ethernet cable). Wireless is far too unreliable for that.

Why do you use WICD, by the way? Is there a problem with the default Network Manager?

---

### Post by Lockheed on 2010-02-18
If only it was so simple...
All WiFi networks around are on channel 11, 10 and 9. Besides, I have this problem with any network in the city running on channel lower than 6-7. 
It seems as the lower the channel, the worse the connection.

---

### Post by Pjotr123 on 2010-02-19
And how about that firmware update?

---

### Post by Lockheed on 2010-02-19
What about it? It happens on 10 different routers in different parts of the city. Besides, it is the newest firmware, anyway.

---

### Post by Pjotr123 on 2010-02-19
You're using WICD. Does your wireless chipset have the same problem when you use Network Manager instead? Try it with the LiveCD.

If so, it may be a driver problem. In that case, you may want to try the newest Atheros driver. Try the latest alpha LiveCD of 10.04, that'll probably have a new Atheros driver on board. FYI: my netbook has an Atheros wireless chipset as well, and has no such problems at all. Runs fine on the default Ubuntu ath5k driver in both 9.04 and 9.10.

---

### Post by Lockheed on 2010-02-19
I was using WICD with low channel wifi networks before with no problems. Besides, 3-4 months ago on the same system I had no such problems anyway.

What do you mean by "try the newest Atheros driver"?

---

### Post by DrMelon on 2010-02-19
> **Lockheed said:**
> 
What do you mean by "try the newest Atheros driver"?

Well, I don't know. He might mean "buy six elephants and keep them in your garden", what do you think?

---

### Post by Lockheed on 2010-02-19
> **DrMelon said:**
> Well, I don't know. He might mean "buy six elephants and keep them in your garden", what do you think?

Since in the first post I said
```
so I updated to the newest compat-wireless
```
without further elaboration on his side your sarcasm is not very well placed, is it?

---

### Post by Pjotr123 on 2010-02-19
Check the Madwifi project for the latest driver. Means compiling yourself.
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

But why don't you give feedback about the results with Network Manager? The problem may very well be WICD related. I really can't help you, if you don't follow my troubleshooting advice.

---

### Post by Lockheed on 2010-02-19
I think Madwifi has been discontinued about 2 years ago.
I will get Ubuntu livecd and check this out.

---

### Post by Pjotr123 on 2010-02-19
> **Lockheed said:**
> I think Madwifi has been discontinued about 2 years ago.


I don't think so. See the dates of the latest snapshots: the latest are from february 2010.

Anyhow, I'm curious what Network Manager will do.

---

### Post by Lockheed on 2010-02-19
Somewhat to my surprise, exactly the same problem occurred on live cd of Ubuntu 9.04 64bit. I will now test 9.10

to my knowledge, Madwifi has been discontinued and incorporated into ath5k project which is now official part of Ubuntu.

EDIT:
I forgot to add, everything works perfectly well under Windows.

---

### Post by Lockheed on 2010-02-19
Well, Ubuntu 9.10 works fine as well.
The question is why?

---

### Post by Pjotr123 on 2010-02-20
> **Lockheed said:**
> Well, Ubuntu 9.10 works fine as well.
The question is why?

Several possibilities, but the most likely candidate is the version of Network Manager in 9.10. Apparently improved. Another thing that struck me: you apparently use a non-default 2.6.31-kernel in 9.04: that's no recipe for stability, of course, because 9.04 was built around an older kernel version.

Well, at least you have a practical solution for your problem now: use 9.10 with Network Manager instead of WICD. :)

I must say that Ubuntu 9.10 is, in my experience, surprisingly good. Considering the amount of fundamental innovations "under the hood", I would have expected Karmic to be rather unstable and buggy. But I've found it to be stable, reliable and pleasant to use, especially so after the first rounds of updates in november/december.

---

### Post by Lockheed on 2010-02-20
9.10 is not an option to me. I would lose months of customization.

I am sure newer Network Manager is not the solution here. If it was, WICD would be working fine.

---

### Post by Lockheed on 2010-02-20
I tried installing newest MadWiFi according to this guide:
[http://ubuntuforums.org/showthread.php?t=1163380](http://ubuntuforums.org/showthread.php?t=1163380)
but once it is compleated, I have no wireless interface in **ifconfig** and, nedeless to say, I am unable to see nor connect to any wireless networks.

---

### Post by Lockheed on 2010-02-23
Newest kernel seems to perform somewhat better. I am able to use internet from channel 3 upwards. 

However, on channel 1 I still get pings above 50 000.

---

### Post by Lockheed on 2010-06-07
I have since upgraded to 10.04 and 2.6.34 but the problem continues.

**Oh, Ubuntu - the most ridiculous operating system I have ever known.**
The day I switch to Arch will be incomparably happier than the day I switched from Windows to Ubuntu. I just wish I knew Arch before I decided to go for this menace from South Africa.

---

