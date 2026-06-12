---
title: "Install sees striped raid"
date: 2011-07-19
forum: General Help
---

### Post by LorenG on 2011-07-19
Hello, I have an old PC where I had installed WinXP in a raid 0 setting. With that configuration, after a long search, I could not find a way to install ubuntu on the raid (nvidia chipset) so I gave up the idea. 
Recently I had to reinstall the O/S so this time I thought to be smarter and dismantled the raid and installed Win XP on one disk only and left the second empty. Went to install Ubuntu 11.04 and when I got to the point it looks like now Ubuntu only sees the two drives as one unformatted striped drive.. is there an option to tell Ubuntu that I do not want it to install using a raid 0 configuration and get to install it in dual boot with windows? Why is doing that, I do not understand what is happening..:confused:

---

### Post by Quackers on 2011-07-19
You may need to delete the raid data left from the array. ```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` Obviously the above refers to your 2 hard drives as Linux sees them. If yours aren't sda and sdb, change the commands accordingly.

---

### Post by LorenG on 2011-07-19
> **Quackers said:**
> You may need to delete the raid data left from the array. ```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` Obviously the above refers to your 2 hard drives as Linux sees them. If yours aren't sda and sdb, change the commands accordingly.

thanks a lot for the advice, I will try that and then post the result. :D

---

### Post by Quackers on 2011-07-19
Good luck :-)

---

### Post by LorenG on 2011-07-20
Thanks, it worked perfectly! :)

---

### Post by Quackers on 2011-07-20
Excellent :-)

---

