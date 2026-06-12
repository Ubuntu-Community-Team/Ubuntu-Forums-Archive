---
title: "Konsole: run automated commands every 10 seconds?"
date: 2006-05-20
forum: General Help
---

### Post by electronate on 2006-05-20
So I installed KDE successfully and have been messing around with Knosole...

Anyone have advice for running a command less than every minute with a script, or perhaps cron?  

I really don't know much about crontab -e, other than it doesn't work when i throw in a command, and an extra new line.

I tried a crazy perl script I modified with some code I found online, but it stop executing after about 5 minutes.  Oh yeah, and it bogged down the system heavily.  perl. pffft. ;)

Any suggestions would help... really, anything.:-k

---

### Post by kaamos on 2006-05-20
```
while(true); do *yourcommandshere*; sleep 10; done
```

---

### Post by rich.bradshaw on 2006-05-21
try apt-get install kcron,

its a gui for cron... makes it a lot easier to use, if thats what you are having problems with. I don't know if it goes by seconds, i think the minimum is minutes.
anything
You could try something like : while(true); do echo "hello"; sleep 10; done, where you put your command after the do. What are you trying to do?

---

