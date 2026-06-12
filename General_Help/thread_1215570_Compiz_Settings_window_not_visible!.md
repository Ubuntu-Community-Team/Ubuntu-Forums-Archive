---
title: "Compiz Settings window not visible!"
date: 2009-07-17
forum: General Help
---

### Post by rocket16 on 2009-07-17
Hello all. I am in a funny problem today. Actually, I am just a novice in Linux, amd am learning a lot from this Golden Forum. So, to make Ubuntu look even better than Windows Vista, I have installed KDE in Ubuntu. Now, to make GNOME look better, I am using Compiz Effects. To make the Windows Transparent, I have set Opacity to standard levels. But accidentally, I have set the value to 0 for the Compiz Window itself, making it no longer visible! :( So, is there any way I can make it visible once again (from Shell or others)? Any one to answer is heartily welcome.

---

### Post by NightwishFan on 2009-07-17
Try disabling compiz and the resetting the values in ccsm (which should be visible). Then reenable.

---

### Post by pmlxuser on 2009-07-17
Compiz store its settings in  /home/user_name/.config/compiz/compizconfig/
There is a file called default.ini
you can edit it using your defaul editor to set the right setting
or you can just delete it to start all over

regards

---

### Post by rocket16 on 2009-07-18
Guys, Thanks to all! I have solved the problem, which could never had been possible without your help! Thanks again (I solved the probem by disabling Transparency from Simple Compiz-Settings-Manager).

---

