---
title: "Cron Problem"
date: 2006-04-29
forum: General Help
---

### Post by Anilkumar on 2006-04-29
Hello everybody,

I have some problem with cron.

This is my crontab

01 16 * * *	/usr/bin/pon dsl-provider
03 16 * * *	/usr/bin/ktorrent


Here pon dsl-provider worked and  i got the internet connected.but ktorrent did not launch and i do not see any window of the ktorrent.so please fix me and guide me

Do i need any shell scripts to run this ktorrent?
If yes please provide me becoz i am poor in programming of shell?

plzzzzzz guide me and solve the problem

---

### Post by Sutekh on 2006-04-29
Is ktorrent a graphical program?  If so the problem is likely that you need to tell crontab and ktorrent where it is going to run, ie what display.

Try changing your crontab to look like this
```
03 16 * * * export DISPLAY=:0 && /usr/bin/ktorrent
```

---

### Post by Anilkumar on 2006-04-29
Thank u it's working

---

