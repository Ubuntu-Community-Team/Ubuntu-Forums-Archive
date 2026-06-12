---
title: "Tor daemon shuts down by itself"
date: 2012-04-27
forum: General Help
---

### Post by tripialos on 2012-04-27
Hi guys.

I have installed Tor with polipo on my new VPS and i am facing a strange issue here.

When i run the command:

```
$service tor status
```

I get the result:

```
tor is not running
```

I then start tor and get the following results:

```

root@myserver:~# service tor status
tor is not running
root@myserver:~# service tor start
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Apr 27 13:18:14.369 [notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 27 13:18:14.370 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 27 13:18:14.370 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 27 13:18:14.370 [notice] Opening Control listener on /var/run/tor/control
done.
root@myserver:~# service tor status
tor is running

But after 2 minutes

root@myserver:~# service tor status
tor is not running



```

Anyone has any idea why this might be happening? Is there any tor daemon log in order to study any errors or messages of why tor is down ?


System: Ubuntu 11.04 Server 32bit


Thanks in Advance

---

### Post by tripialos on 2012-04-28
Anyone?

---

