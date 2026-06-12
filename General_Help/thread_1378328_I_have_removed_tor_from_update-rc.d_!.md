---
title: "I have removed tor from update-rc.d !"
date: 2010-01-11
forum: General Help
---

### Post by s.l.i.m on 2010-01-11
hi,

i have problem with vidalia/tor. so i search on google, type some command. One of these is : **sudo update-rc.d -f tor remove**. 

Later i can start tor with commands.
Now tor won't start
here is the error message :

> 
alaa@pc-alaaa:~$ sudo /etc/init.d/tor start
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Jan 11 16:47:40.772 [notice] Tor v0.2.2.6-alpha (git-1ee580407ccb9130). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jan 11 16:47:40.773 [warn] Skipping obsolete configuration option 'Group'
Jan 11 16:47:40.773 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Jan 11 16:47:40.773 [notice] Opening Socks listener on 127.0.0.1:9050
Jan 11 16:47:40.773 [notice] Opening Socks listener on 127.0.0.1:9050
Jan 11 16:47:40.774 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jan 11 16:47:40.774 [notice] Closing partially-constructed listener Socks listener on 127.0.0.1:9050
Jan 11 16:47:40.774 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 11 16:47:40.774 [err] Reading config failed--see warnings above.
alaa@pc-alaaa:~$ 


So how to repair it ?

---

