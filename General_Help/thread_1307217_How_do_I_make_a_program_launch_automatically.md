---
title: "How do I make a program launch automatically"
date: 2009-10-30
forum: General Help
---

### Post by robofighter on 2009-10-30
I am going to making a server that will various things.

I want the server to start and launch programs and commands at a certain time.

I know the commands on how to do them through the terminal, but I don't know how to auto-launch them.

Some of the things I want it to do is,
Launch a magic packet to autoboot my main computer at 6 AM
At 11 am it will update clamav.
at noon it will scan the shared folders
at 11 pm, it will download and install updates.
at 12 am it will restart computer.

If possible, I want to know how to do these settings through the command line.

---

### Post by sickly on 2009-10-30
for these kinds of things you will need some shell scripts to carry out these comands for you. Maybe someone here can be nice enough to write one for your exact needs. But in the mean time if you would like you can learn more about it here
 
[http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)
 
Hope this helps

---

### Post by robofighter on 2009-10-31
hmm, I just found a program calle gnome schedule or something like that that could do it.

But what about about programs that will need administrator access like the updates and reboot

---

### Post by Bender2k14 on 2009-10-31
You could use [cron]("http://en.wikipedia.org/wiki/Cron").

---

### Post by robofighter on 2009-10-31
How do I use cron?

Anyone got a guide?

---

