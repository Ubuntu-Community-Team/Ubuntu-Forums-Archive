---
title: "Firefox won't run"
date: 2010-01-30
forum: General Help
---

### Post by Raian the Fallen on 2010-01-30
Good god, I'm having ALL the luck. xD

Anyway, I installed Ubuntu normally. Whenever I try to run Firefox for the first time, it loads for a bit, then it crashes. Every time. I tried reinstalling it, and the isntallation was fine. I managed to connect properly. But it won't run.

---

### Post by gate on 2010-01-30
First thing you will need is the output to help diagnose the problem. Try running the command ```
firefox
``` from the commmand line. 


You might also try safe mode with the command 
```
firefox -safe-mode
```

I had a problem where firefox had similar symptoms, but it was due to an NFS file system peculiarity.

---

### Post by lovinglinux on 2010-01-30
Does it crash on every page or on specific pages? What errors do you get on the terminal?

[This might help]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-%28grey%29-frequently-2"), although it could be pulseaudo or other application interfering with Firefox.

I presume you don't have any extensions installed right or are you using your old Firefox profile from Windows? If you are using an old profile or if you have imported your settings, try to [create a new profile](http://lovinglinux.megabyet.net/?page_id=220#Profiles-1).

---

