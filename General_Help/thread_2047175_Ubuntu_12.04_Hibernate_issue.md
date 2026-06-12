---
title: "Ubuntu 12.04 Hibernate issue"
date: 2012-08-24
forum: General Help
---

### Post by Neil92 on 2012-08-24
Yesterday I installed Ubnutu 12.04 using Wubi.

I enabled Hibernate, but whenever I use it I get this error:

> [137.47655] PM: Not enough free swap

I tested  sudo pm-hibernate, but it just leaves my monitor black with the computer running

---

### Post by PhantomTurtle on 2012-08-24
How much swap space do you have and how much RAM do you have. Usually your swap space must be at least double the size of your RAM(eg. RAM = 2GB, swap = 4GB). Also hibernate was disabled in Ubuntu since 12.04 since it doesn't really work all the time. When using sudo pm-hibernate and hibernation doesn't work then that means that will not work on your computer.

---

### Post by Neil92 on 2012-08-24
> **PhantomTurtle said:**
> How much swap space do you have and how much RAM do you have. Usually your swap space must be at least double the size of your RAM(eg. RAM = 2GB, swap = 4GB). Also hibernate was disabled in Ubuntu since 12.04 since it doesn't really work all the time. When using sudo pm-hibernate and hibernation doesn't work then that means that will not work on your computer.

After installing Gparted, I got 110.87 GiB used, 187.21 GiB ununsed.

I have 3 GiB memory

so since the command "Sudo pm-hibernate" doesn't work (like I said, it just makes the screen black while my computer continues to run), you're telling me I'm out of luck?  Jeez, this OS has been a huge disappointment thus far.

---

### Post by Rexilion on 2012-08-24
Could you post the output of the following command please?

> free -m

Should tell us everything about swap status.

---

### Post by Neil92 on 2012-08-24
> **Rexilion said:**
> Could you post the output of the following command please?



Should tell us everything about swap status.

Total 3023
Used 2699
Free 324
Swap total: 255
Swap Free: 255

---

### Post by PhantomTurtle on 2012-08-24
> **Neil92 said:**
> Total 3023
Used 2699
Free 324
Swap total: 255
Swap Free: 255

So you have around 3GB swap them. Which is the same size of your RAM. That may be the problem. Usually the installer goes for 2x the size of the RAM. Also the reason hibernate was disabled was because sometimes Ubuntu would not wake up and you would loose your data. I recommend that you do not using hibernate. However you might want to do some more tests, because it might work on your computer.

---

### Post by Rexilion on 2012-08-25
> **Neil92 said:**
> Swap Free: 255

There is your issue :) . You have 3GiB of memory and you use almost all of your swap. How is that possible? Are you running something 'intensive'?

---

