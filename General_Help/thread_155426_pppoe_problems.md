---
title: "pppoe problems"
date: 2006-04-05
forum: General Help
---

### Post by fouadk on 2006-04-05
hey everyone, i have a pppoe connection that works just great in windows...
i used pppoeconf to configure it in ubuntu 5.10 and it worked or a while but suddently it wouldnt connect anymore, so i opened a terminal and used pon dsl-provider and plog and here is the result i got:
```

fouad@turbo:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
fouad@turbo:~$ sudo plog
Apr  3 19:34:17 localhost pppd[15569]: Connect: ppp0 <--> eth0
Apr  3 19:34:17 localhost pppd[15569]: Couldn't increase MTU to 1500
Apr  3 19:34:17 localhost pppd[15569]: Couldn't increase MRU to 1500
Apr  3 19:34:17 localhost pppd[15569]: Couldn't increase MTU to 1500
Apr  3 19:34:17 localhost pppd[15569]: Couldn't increase MRU to 1500
Apr  3 19:34:17 localhost pppd[15569]: Remote message: Dialed NAS not allowed.^J
Apr  3 19:34:17 localhost pppd[15569]: PAP authentication failed
Apr  3 19:34:17 localhost pppd[15569]: Couldn't increase MTU to 1500
Apr  3 19:34:17 localhost pppd[15569]: Couldn't increase MRU to 1500
Apr  3 19:34:17 localhost pppd[15569]: Connection terminated.
fouad@turbo:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
fouad@turbo:~$ sudo plog
Apr  3 19:34:22 localhost pppd[15599]: Couldn't increase MRU to 1500
Apr  3 19:34:22 localhost pppd[15599]: Connection terminated.
fouad@turbo:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
fouad@turbo:~$ sudo plog
Apr  3 19:34:24 localhost pppd[15627]: Couldn't increase MRU to 1500
Apr  3 19:34:24 localhost pppd[15627]: Connection terminated.
fouad@turbo:~$

```
please help me coz im sick of all the popups and all the stupid things that u get when u connect to the net using windows](*,)
and please elaborate ur answers coz im not a guru , im more a newbie:D

---

