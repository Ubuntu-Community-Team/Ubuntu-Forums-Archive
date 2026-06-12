---
title: "Laptop Restarting after every few minutesb"
date: 2010-06-07
forum: General Help
---

### Post by arjunbajaj on 2010-06-07
Hey Guys,

My Laptop only contains Ubuntu 10.04 and while installing it i had to add some parameters to start installing and then make them permanent...... It was [Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes").....

So now after a few days of using my laptop...... It restarts every few minutes....

So what can i do..... to prevent the restart

---

### Post by ThesaurusRex on 2010-06-07
Just so we're clear: It *was* working fine, but now, a few days later, it restarts every few minutes?

---

### Post by arjunbajaj on 2010-06-07
Yes, You are right....

So is there any thing i can do???

thnx....

---

### Post by Mark Phelps on 2010-06-07
There have been numerous reports of laptops overheating with 10.04 -- doesn't mean yours is one of them, but frequent restarts are most often indicators of heat-related or memory-related problems.

You can boot from an Ubuntu LiveCD and run the memory test to check out your memory.

You can also install lm-sensors, run "sudo sensors-detect" to setup the sensors, and then run "sensors" to periodically check the component temperatures.

If your laptop is overheating, you've got a serious problem that runs the risk of burning out components.

---

### Post by arjunbajaj on 2010-06-08
Acutually My Laptop is IBM ThnikPad R51 which is about 4 years old.....

It doesn't even support boot of i686 architecture (tried by booting fedora).....

And It was not even booting till i put the parameters the Lucidi8xxFreezes bug told me to do....

And I have increased the ram from 512 MB to 1.4 GB......

And It heats too much so i have to use a cooling stand.....
And even after using the cooling stand it reboots sometimes.....

---

### Post by Mark Phelps on 2010-06-08
IF you want to monitor the laptop temperatures, you have to follow the instructions I provided.

---

