---
title: "multiple applications from 1 terminal"
date: 2009-12-27
forum: General Help
---

### Post by Groundswell on 2009-12-27
hey guys, when launching an application or script to launch an app from terminal (i'm only concerned about xserver apps here) , the terminal becomes locked to that job. So basically i can't launch or do anything from that same terminal until the job is finished. Is there anyway to continue using a terminal after launching something, and maybe direct application output to a designated terminal?

I know i could just keep opening new tabs, but thats relatively the same as opening new terminals

---

### Post by Cheesemill on 2009-12-27
Just add a " &" to your command, for example:
```
apt-get update &
```
The & will return focus to the shell immediately instead of waiting for the command to finish.

---

### Post by Groundswell on 2009-12-27
thankyou thankyou thankyou =D>

---

### Post by lorsen on 2009-12-27
You can also press CRTL-z after you started an application. This stopps (pauses) the application and gives you the possibility to type again in the terminal. By typing fg or bg you can decide if the application runs afterwards in foreground (terminal blocked) or in background (same as using & after command, allows you to use terminal further on).

---

