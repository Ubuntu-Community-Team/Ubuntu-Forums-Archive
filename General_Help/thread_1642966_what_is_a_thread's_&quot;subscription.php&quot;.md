---
title: "what is a thread's &quot;subscription.php&quot;?"
date: 2010-12-11
forum: General Help
---

### Post by lazylew on 2010-12-11
Today Ubuntu-forums is really slow for some reason, and has strange behaviour; when I subscribe to a thread, there's a pop-up that asks me where I want to download "subscription.php"
I've never seen this before - what's happening here?

EDIT: by "really slow" I mean any tab on Ubuntu forums takes literally minutes to load, whereas I have another 17 tabs open that are super quick as normal.

---

### Post by WorMzy on 2010-12-11
I've seen the behaviour on other websites when the server is overloaded; the file it prompts you to download is a headerless blank file, which is why it asks you about it. What's supposed to happen is the webserver processes the php file(s) on the server, then returns text/html (or application/xhtml+xml) content to your web browser to display.

I'm not experiencing any such behaviour, so I can't say for sure that this is what is happening to you. Check your network is configured correctly, and see if you can ping 91.189.94.12 (the ubuntu forum's IP address)

---

### Post by lazylew on 2010-12-11
> **WorMzy said:**
> I've seen the behaviour on other websites when the server is overloaded; the file it prompts you to download is a headerless blank file, which is why it asks you about it. What's supposed to happen is the webserver processes the php file(s) on the server, then returns text/html (or application/xhtml+xml) content to your web browser to display.

I'm not experiencing any such behaviour, so I can't say for sure that this is what is happening to you. Check your network is configured correctly, and see if you can ping 91.189.94.12 (the ubuntu forum's IP address)Indeed the files are blank, so I'll delete them. I'm not sure what output is expected from ping, but here it is:
```
ping 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=50 time=20.1 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=50 time=21.6 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=50 time=19.3 ms
64 bytes from 91.189.94.12: icmp_req=4 ttl=50 time=20.2 ms
64 bytes from 91.189.94.12: icmp_req=5 ttl=50 time=21.2 ms
64 bytes from 91.189.94.12: icmp_req=6 ttl=50 time=19.6 ms
64 bytes from 91.189.94.12: icmp_req=7 ttl=50 time=29.5 ms
64 bytes from 91.189.94.12: icmp_req=8 ttl=50 time=20.2 ms
64 bytes from 91.189.94.12: icmp_req=9 ttl=50 time=19.5 ms
64 bytes from 91.189.94.12: icmp_req=10 ttl=50 time=20.4 ms
64 bytes from 91.189.94.12: icmp_req=11 ttl=50 time=20.4 ms
64 bytes from 91.189.94.12: icmp_req=12 ttl=50 time=20.0 ms
64 bytes from 91.189.94.12: icmp_req=13 ttl=50 time=20.6 ms
64 bytes from 91.189.94.12: icmp_req=14 ttl=50 time=20.5 ms
64 bytes from 91.189.94.12: icmp_req=15 ttl=50 time=21.3 ms
64 bytes from 91.189.94.12: icmp_req=16 ttl=50 time=18.9 ms
64 bytes from 91.189.94.12: icmp_req=17 ttl=50 time=20.5 ms
64 bytes from 91.189.94.12: icmp_req=18 ttl=50 time=20.0 ms
64 bytes from 91.189.94.12: icmp_req=19 ttl=50 time=21.3 ms
64 bytes from 91.189.94.12: icmp_req=20 ttl=50 time=30.4 ms
64 bytes from 91.189.94.12: icmp_req=21 ttl=50 time=20.7 ms
64 bytes from 91.189.94.12: icmp_req=22 ttl=50 time=19.5 ms
64 bytes from 91.189.94.12: icmp_req=23 ttl=50 time=20.0 ms
64 bytes from 91.189.94.12: icmp_req=24 ttl=50 time=18.9 ms
64 bytes from 91.189.94.12: icmp_req=25 ttl=50 time=19.8 ms
64 bytes from 91.189.94.12: icmp_req=26 ttl=50 time=21.0 ms
^C
--- 91.189.94.12 ping statistics ---
26 packets transmitted, 26 received, 0% packet loss, time 25035ms
rtt min/avg/max/mdev = 18.943/21.016/30.489/2.705 ms
```
I did CTRL-c to stop it, guessing it would otherwise go on forever.
BTW the forum is now at normal speed again, so probably it was like you say an overload of users and I won't panic ;)

---

