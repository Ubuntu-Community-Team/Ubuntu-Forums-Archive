---
title: "High CPU usage during screen off"
date: 2012-05-15
forum: General Help
---

### Post by vishnumrao on 2012-05-15
Just built three AMD A8-3870k based ITX machines with Asrock A75m-itx mobo and 8 GB RAM.

Problem: As soon as the screen turns off as part of the power savings, I started noticing the significantly noisier fan sound from the machine. I turned ON System Monitor and left the computer to go to screen off state. 

I found the cause for the high fan noise. Please see the screenshot that shows one core being tied to 100 % cpu usage.  In the screenshot the core (in blue) is tied 100% until I moved the mouse to bring it back to use. Thats when the cpu usage comes down. What could be the reason for this? All the three machines show the same problem. 

Two systems have fresh installs of Ubuntu 12.04 64 bit and one was upgraded from Ubuntu 11.10 64 bit.Any ideas my fellow ubuntueers?

---

### Post by mastablasta on 2012-05-15
what are other system specs? 
have you checked commands top or htop to see what process is cloging up the CPU core?

---

### Post by roelforg on 2012-05-15
Open a terminal and run top
Observe what uses the most cpu (thats how it's sorted).

---

### Post by brainwash on 2012-05-15
If you are using **compiz**, take a look at this thread:

[http://ubuntuforums.org/showthread.php?p=11936668](http://ubuntuforums.org/showthread.php?p=11936668)

---

### Post by vishnumrao on 2012-05-15
All, I think the thread brainwash pointed me to is the same problem I have. Thanks to all for the help.

---

