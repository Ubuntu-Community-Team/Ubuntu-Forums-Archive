---
title: "pppoe dialing internet problems"
date: 2006-04-03
forum: General Help
---

### Post by fouadk on 2006-04-03
hey everyone, i have a pppoe connection, i first used pppoeconf to configure it and it worked for a while and it connected automatically whenever i started ubuntu but a week ago it wouldnt work no matter what, i write in a terminal the following and it keeps repeating no matther what without any result.](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 
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

```
what shall i do, in damn windows the connection works perfectly... please help with complete details coz im a newbie

---

