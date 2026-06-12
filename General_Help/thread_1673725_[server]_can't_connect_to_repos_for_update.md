---
title: "[server] can't connect to repos for update"
date: 2011-01-22
forum: General Help
---

### Post by LGN on 2011-01-22
Hello all,

I just recently installed ubuntu server on a PC that'll be our home server.

I got it connected to the network but I can't update the repos with apt or aptitude.
It stops at something about security.ubuntu.com
How do I fix this? I need to install software

---

### Post by thomas144 on 2011-01-22
Hi there LGN, I think I might be able to lend a hand. Can you do me a favor and post the output of the command you're trying to run? Thank you.

---

### Post by LGN on 2011-01-22
1- I used sudo apt-get update
2- how do I do that? It's ubuntu server, I can't paste into a browser

---

### Post by thomas144 on 2011-01-22
Oh, okay then. Stupid me. But can you please be a little more specific when you say that it stop at security.ubuntu.com? Does it just hang?

---

### Post by LGN on 2011-01-22
I'll rerun it and tell you some things that I see, but I might not see all of it

$sudo apt-get update

i see

0% [Connecting to us.archive.ubuntu.com (91.189.88.461)] [Connecting to security

then a lot of scrolling stuff
a whole bunch of things like 

Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/[repo name here] amd64 packages
Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166.89
16% [Connecting to us.archive.ubuntu.com (91.189.92.169)]

then a lot of scrolling stuff
and a bunch of things like w: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/)[repo name here]/binary-amd64/Packages.gz Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

Hope this helps!

---

### Post by thomas144 on 2011-01-22
Hmm.....
I'm not sure what could cause this, other than a problem with your connection to the network or the Internet. If you run
```
ping ubuntu.com
```
What happens?

---

### Post by LGN on 2011-01-23
I ran an altered version of that so it would only ping 3 times

Here's what I got

```
$ping -c 3 ubuntu.com
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=1 ttl=47 time=88.5
ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=2 ttl=47 time=87.8
ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_req=3 ttl=47 time=87.7
ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rit min/avg/max/ndev = 87.788/88.061/88.533/0.479 ms
```

It seems the internet works fine, but APT doesn't want to connect.
I tried updating APT again now and it still didn't work.

---

