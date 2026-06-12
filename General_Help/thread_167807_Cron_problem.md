---
title: "Cron problem"
date: 2006-04-29
forum: General Help
---

### Post by Anilkumar on 2006-04-29
Hello everybody,

I have some problem with cron.

This is my crontab

01 16 * * * /usr/bin/pon dsl-provider
03 16 * * * /usr/bin/ktorrent


Here pon dsl-provider worked and i got the internet connected.but ktorrent did not launch and i do not see any window of the ktorrent.so please fix me and guide me

Do i need any shell scripts to run this ktorrent?
If yes please provide me becoz i am poor in programming of shell?

plzzzzzz guide me and solve the problem

---

### Post by Anilkumar on 2006-04-29
I am using kcron

---

### Post by GeneralZod on 2006-04-29
ktorrent will fail due to a lack of connection to the X-server.

Try replacing 

```

/usr/bin/ktorrent

```

with

```

export DISPLAY=:0; /usr/bin/ktorrent

```

---

### Post by [S|G] on 2006-04-29
Try adding this on the first line in your crontab:

DISPLAY=:0.0

Then you should have something like:
```

DISPLAY=:0.0
01 16 * * * /usr/bin/pon dsl-provider
03 16 * * * /usr/bin/ktorrent

```

---

### Post by Anilkumar on 2006-04-29
Thank you it i working .Thank you very much

---

