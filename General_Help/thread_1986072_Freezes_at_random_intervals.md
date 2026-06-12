---
title: "Freezes at random intervals"
date: 2012-05-24
forum: General Help
---

### Post by J V on 2012-05-24
I thought my freezes were the result of overclock instability, despite rigorous stability tests, however now I'm not so sure:
```
 May 24 00:39:01 fatherboard CRON[4547]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
```This is the last line in my /var/log/syslog before a freeze almost every time.

What does it do and could it be responsible for freezing my system?

**Edit:** Nvm, just a botched stability test

---

