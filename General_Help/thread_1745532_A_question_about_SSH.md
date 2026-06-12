---
title: "A question about SSH"
date: 2011-05-01
forum: General Help
---

### Post by TheHimself on 2011-05-01
If you start an ssh session and run a program on the remote server, is the program terminated if you close the session? Is there any way to keep the program running when you don't want to wait for it to finish? (Maybe using  & ?)

---

### Post by nothingspecial on 2011-05-01
Sure you can

ssh to your remote box

type ```
screen
``` (install it if you don't have it)

start the process

press Ctrl-A then D

Then you can log out

Fly halfway around the world.

ssh into the remote box from a completely different computer in another country.

type ```
screen -r
```

There's your process chugging away.

---

### Post by HermanAB on 2011-05-01
...or if you don't have screen, you can schedule tasks using the 'at' or 'cron' daemons.

---

### Post by Lars Noodén on 2011-05-01
**screen** is very powerful and can be overkill in some cases.
[nohup](http://linux.die.net/man/1/nohup) is very simple to use and make your process immune to the hangup signal it will get when you close SSH.  If you are working in a kerberos environment then you'll need to look at **pagsh** instead.

---

