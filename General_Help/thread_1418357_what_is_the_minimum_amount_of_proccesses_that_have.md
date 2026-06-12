---
title: "what is the minimum amount of proccesses that have to be run?"
date: 2010-02-28
forum: General Help
---

### Post by drink_stir on 2010-02-28
what is the minimum amount of processes that can be run and still keeping stable?  I have what looks like over 100 processes running and my computer is lagging pretty bad. attached is an output of ```
ps -A
```

and it comes and goes with the cpu usage.  cpu1 will run at like 9 or 10 percent idle while cpu2 will run at 100 percent all the time. im not sure whats going on. but id hate to have to start from scratch again beins i just got it set up the way i want it.  and the network activity keeps having spikes when im not online. ive scanned with multiple port scanners and nothing seems out of the norm.

---

### Post by Barriehie on 2010-03-01
ps aux would be much more beneficial!

---

### Post by 3rdalbum on 2010-03-01
The network spikes can be normal depending on your exact computer.

There is a program that is using too much of your CPU power. You can find this program by going to System > Administration > System Monitor and sorting the list by "CPU %". Kill it and don't run it again, and your computer will regain its speed.

The number of processes is not a problem. Only one of the processes is.

---

### Post by drink_stir on 2010-03-01
ps aux has alot more information than -A thanx. i got the usage down.another question i have is about the users. there are about 7 or 8 users among them is root (normal) daemon (normal i think) me , me other, gdm and then theres 107 and 102. i never defined these users. are they normal?

---

### Post by undecim on 2010-03-01
> **drink_stir said:**
> ps aux has alot more information than -A thanx. i got the usage down.another question i have is about the users. there are about 7 or 8 users among them is root (normal) daemon (normal i think) me , me other, gdm and then theres 107 and 102. i never defined these users. are they normal?

Yes perfectly normal.The system uses them to run processes with a separation of power. It's a good security setup, because if someone, for example, finds a way to execute abitrary code from GDM, that code is run as gdm, rather then root, and so there isn't much that an attacker could do with that.

---

