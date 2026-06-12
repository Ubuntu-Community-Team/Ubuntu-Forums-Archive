---
title: "aptitude problem"
date: 2010-04-18
forum: General Help
---

### Post by FiskFisk33 on 2010-04-18
i cant install anything on my fresh install through aptitude, it just returns (113: no route to host). but the network seems to work flawlessly (i'm writing this from the same computer.

for example, trying to install "synergy"
```
Err http://archive.ubuntu.com karmic/universe synergy 1.3.1-6ubuntu1
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113: No route to host)
```

any ideas?

---

### Post by dufftime on 2010-04-18
Proxy settings?  Check out this post:  [http://ubuntuforums.org/showthread.php?t=630132](http://ubuntuforums.org/showthread.php?t=630132)

---

### Post by FiskFisk33 on 2010-04-18
i dont use a proxy no. :(

---

### Post by dufftime on 2010-04-18
Perhaps it's specific to that server.  Can you ping archive.ubuntu.com?  From where I am, it's resolving to prat.canonical.com (91.189.88.45).

---

### Post by FiskFisk33 on 2010-04-18
> **dufftime said:**
> Perhaps it's specific to that server.  Can you ping archive.ubuntu.com?  From where I am, it's resolving to prat.canonical.com (91.189.88.45).

```
fiskfisk33@Tehfisktop ~ $ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.46) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=1 ttl=50 time=40.0 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=2 ttl=50 time=40.2 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=3 ttl=50 time=39.1 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=4 ttl=50 time=36.5 ms
64 bytes from archive.ubuntu.com (91.189.88.46): icmp_seq=5 ttl=50 time=39.4 ms

```

This is the strange part, everything seems to work networkwise except for aptitude.

---

### Post by dufftime on 2010-04-18
Hmm... if you're sure it's not a proxy setting doing this, then it might be related to IPv6.  I Google'd that strange IP you're getting (1.0.0.0) and ran across this bug report.

[https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)

There are a few work-arounds, and it seems to occur more often with wget and/or apt-get.

---

### Post by FiskFisk33 on 2010-04-19
Yay, thanks.
It seems some modems doesnt like ipv6 type dns requests (my modem being one of those), and it seems apt-get and wget is very prone to use them dispite ipv6 being turned off.
The solution (or, well, workaround) was to reroute dns requests directly to opendns (or any other service like it) instead of the modem itself.

Seems to work like a charm so far.

---

