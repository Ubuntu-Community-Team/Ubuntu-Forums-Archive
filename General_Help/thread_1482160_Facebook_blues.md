---
title: "Facebook blues"
date: 2010-05-13
forum: General Help
---

### Post by HuaiDan on 2010-05-13
I don't care about facebook. However, I live in China, where facebook is blocked (one thing the Chinese got right),, and it seems almost every webpage these days is somehow linked or references facebook. When this happens, my browser hangs, waiting for facebook to load until it times out. I'm getting tired of almost every webpage taking minutes to load.

So, how do I stop this locally? I tried routing facebook.com to localhost in my hosts file, but this didn't work. This is ideally what I'd like to do.I also tried to use adblock plus and noscript to do it, but I can't make sense of either.

/etc/hosts:
> *.facebook.com   127.0.0.1

reboot, and ping:

> PING [www.facebook.com](www.facebook.com) (59.24.3.173) 56(84) bytes of data.
^C
--- [www.facebook.com](www.facebook.com) ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6003ms

What did I do wrong?

If anyone has any suggestions, please tell me. If you recommend adblock plus to do this, please give me click-by-click, keystroke-by-keystroke specific instruction how to do so, because I'm a total idiot and can't figure it out. Thank you!

---

### Post by nacho32 on 2010-05-13
use this fire Fox addon called[ block site]("https://addons.mozilla.org/en-US/firefox/addon/3145/") ADDblock plus use to support whole page blocking but from what I read they took it out, go figure, but the other will work.

---

### Post by HuaiDan on 2010-05-13
Thanks, that appears to work, but what's wrong with using the hosts file? I've tried several different configurations, mapping test names to test IPs, and vice-versa, but the hosts file doesn't seem to do anything. Unlike Windows, which checks the hosts file first by default (IIRC), the hosts file in Ubuntu seems to be disabled or something. What's going on there?
Any takers, thank you.

---

### Post by marshmallow1304 on 2010-05-13
Your hosts entry is reversed.  Try this
```
127.0.0.1      facebook.com
127.0.0.1      www.facebook.com
```

You can combine them on one line
```
127.0.0.1      facebook.com     www.facebook.com
```



You'll probably need to reboot for changes to take effect.

---

### Post by HuaiDan on 2010-05-14
OK, now I'm pinging [www.facebook.com](www.facebook.com) at 127.0.0.1, almost there. I say almost because ideally I'd like to block ALL in the facebook domain. However, the hosts file does not seem to support wildcards. For example:

Hosts:

> 127.0.0.1     *.facebook.com

reboot, then ping:

> PING l.facebook.com (8.7.198.45) 56(84) bytes of data.
^C
--- l.facebook.com ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10001ms



Following the Ubuntu Manpage for Hosts, I also tried:

> 127.0.0.1    ALL: .facebook.com

unsuccessfully.

So, save for spelling out every possibility in the facebook domain and mapping to localhost address, is there a way to block the whole facebook domain. I might just have to end up static routing it on my router, if it has that option. I haven't checked...

---

### Post by ParadoxBlue on 2010-05-14
I agree China did get that one right. Facebook is a blight.

---

