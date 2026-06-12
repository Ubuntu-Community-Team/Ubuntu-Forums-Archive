---
title: "help regarding  Tunnel VNC through SSH from a windows machine"
date: 2010-01-04
forum: General Help
---

### Post by Sivaram Nyapathi on 2010-01-04
hi friends 
i'm newbie  to ubuntu , i have a windows laptop with windows 7 on it , and have a desktop which runs ubuntu 9.10 desktop edition and i have a network using dlink router (10/100 fast switch). I was able to successfully do remote desktop using vnc viewer ,but to do that i have to log in manually before doing so . after a bit of googling i came to know about SSH and i have downloaded the openssh-server , x11vnc and tried the following 
this is the tutorial [http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)
but no luck , finally when connecting it shows an error message , connection reset by peer . i have tried many different blogs / video on the web but for some or the other reason they are not working .

   my desktop is on 192.168.1.3 and laptop on 192.168.1.2 and my ADSL router on 192.168.1.1,pls help . [-o<

---

### Post by krunge on 2010-01-04
It is possible to collect x11vnc's printout in a file via the "-o filename" option.  Run x11vnc with something like that, then try connecting via VNC a few times (i.e. reproduce the problem you are seeing) and then attach the file with the output to this thread.

---

### Post by synapsys on 2010-01-04
Have you enabled remote desktop sharing?

System >> administration >> remote desktop

---

### Post by Sivaram Nyapathi on 2010-01-05
Yes i did it. It will not promote user for permission every time , just need to type in password ...

---

