---
title: "Can't connect to Last.fm via lastfmproxy"
date: 2010-08-23
forum: General Help
---

### Post by geoffjay on 2010-08-23
I've used lastfmproxy in the past, 8.04 I think, to access Last.fm streams through mpd but this doesn't appear to work anymore.

- after installation I set my user/pass in /etc/lastfmproxy/config.py
- also set /etc/default/lastfmproxy to auto start
- no other proxy is running on my network
- have a working Last.fm account

When I start using /etc/init.d/lastfmproxy start I get the error: Handshake failed. in the logs.

Has anyone managed to get this to work in Lucid?

Thanks.

---

### Post by geoffjay on 2010-08-23
Some additional output I get when running at command line:

main.py:23: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
[Mon Aug 23 15:02:20 2010]: Starting LastFMProxy 1.3b...
[Mon Aug 23 15:02:20 2010]: Connecting to last.fm server...
[Mon Aug 23 15:02:55 2010]: Handshake failed.
Traceback (most recent call last):
  File "main.py", line 818, in <module>
    p.run(config.bind_address, config.listenport)
  File "main.py", line 758, in run
    self.log_print("DEBUG: " + self.lastfm.info)
TypeError: cannot concatenate 'str' and 'dict' objects

---

### Post by geoffjay on 2010-08-24
As it turns out a firewall access rule was required to forward port 1881 traffic to my machine. Adding that fixed the problem.

---

