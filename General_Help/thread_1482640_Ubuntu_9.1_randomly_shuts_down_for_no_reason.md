---
title: "Ubuntu 9.1 randomly shuts down for no reason"
date: 2010-05-13
forum: General Help
---

### Post by milleja46 on 2010-05-13
When running ubuntu 9.1 on a toshiba a105 s4384 it randomly shuts down without warning. At the time of each i am running one or more of the following: Firefox(newest), Monodevelop(2.2), and pidgn for linux. Can someone please help me?

---

### Post by blazemore on 2010-05-13
Does the system actually shut down (go through the usual shutting down process), or does it simply power off completely?

Does this only occur when you're on battery power?

---

### Post by milleja46 on 2010-05-13
It technically makes the windows i have white squares and shows a blue blackground, then it goes though the process of shutting down after showing a blackscreen and some test i can't really catch and shuts down. But when i go to my windows partition so far it doesn't do the same thing. Any solutions. I'm on the windows one till i can get it fixed. I really need it fixed soon because i am trying to add some more functions to Monodevelop's vb.net binding.......

---

### Post by milleja46 on 2010-05-14
Can someone help me?

---

### Post by obscurant1st on 2010-05-14
i dont know, why dont you look into the log files?? 
I am not sure, try dmesg in terminal

---

### Post by milleja46 on 2010-05-14
What? I'm really confused it shouldn't be doing this yet it does....i think it may be the old age of this computer but i'm not sure. I think the computer is from 2005 or 2006, either way it needs to be replaced. But not sure if that is the cause.......any other suggestions?

---

### Post by 3rdalbum on 2010-05-14
If it's going through the shutdown sequence, it's possible that the CPU is hitting Linux's thermal safety shutdown point.

If you're running any extra software to slow down the CPU fans, try not using that software. Also, take a look at the CPU cooler inside the computer, make sure it isn't clogged with dust. It will be located around about the middle of the motherboard, it's a big metal contraption with a fan on top.

There's also the possibility that the power supply is starting to fade out and triggering some sort of undervolt safety shutdown mechanism in Linux (if one exists).

Have you tried running the 'sensors' program?

```
sudo apt-get install lm-sensors
sudo sensors-detect
watch sensors
```

---

### Post by milleja46 on 2010-05-14
No i haven't probably gonna run that next week because i'm not in ubuntu right now, and i don't understand which of the programs i mentioned could be slowing it down. Which were monodevelop, firefox, and pidgn. I did also have my flashdrive open......but i haven't messed with ubuntu that much so what would i know....

---

