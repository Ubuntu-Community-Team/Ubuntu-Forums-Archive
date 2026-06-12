---
title: "Crontab Show Running Script?"
date: 2009-12-23
forum: General Help
---

### Post by FiniteRed on 2009-12-23
Hi Everyone

I have a verbose script that is run from cron on a daily basis, this works fine. However the script is run without showing anything on the screen. Is there a way that I can get the script to output to a terminal so I can see its progress? (it contains progress echos).

Ideally I would like to get the script to output to the same terminal every day so I get a list of all of the backup jobs (attempted, failed and completed) build up in the terminal

Many thanks

FR

---

### Post by BenAshton24 on 2009-12-23
Why not store the output to a log and then monitor it with
```
tail -f log
```

---

### Post by dcstar on 2009-12-23
> **FiniteRed said:**
> Hi Everyone

I have a verbose script that is run from cron on a daily basis, this works fine. However the script is run without showing anything on the screen. Is there a way that I can get the script to output to a terminal so I can see its progress? (it contains progress echos).

Ideally I would like to get the script to output to the same terminal every day so I get a list of all of the backup jobs (attempted, failed and completed) build up in the terminal


```
command-whatever > /dev/tty1
```

---

