---
title: "Ajenti broken all of a sudden"
date: 2012-08-19
forum: General Help
---

### Post by alek66 on 2012-08-19
I just finished installing my home server with lubuntu, and I installed AJENTI to do some monitoring.

Ajenti worked fine until today I installed Python-beautifulsoup package, did a reboot, and ajenti stop working.

When I did a sudo service ajenti stop i got:
pidfile /var/run/ajenti.pid does not exist. Daemon not running?

So I tried to started to get it to run with

aleza@Deathstar:~$ sudo service ajenti start
Starting Ajenti
aleza@Deathstar:~$ sudo service ajenti stop
Stopping Ajenti
pidfile /var/run/ajenti.pid does not exist. Daemon not running?
aleza@Deathstar:~$ 

But it didn't work....

any ideas?

---

