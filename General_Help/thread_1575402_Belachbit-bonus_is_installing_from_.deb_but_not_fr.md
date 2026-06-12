---
title: "Belachbit-bonus is installing from .deb but not from repos"
date: 2010-09-15
forum: General Help
---

### Post by kema_u on 2010-09-15
Hi! I am using Ubuntu 10.04 32 bit. I installed from repos the Bleachbit. But when i try to install the bonus package it writes : "Sorry, 'bleachbit-bonus' is not available for this type of computer (i386)." But i can install the bonus package properly (and it works) by downloading from official web site of Bleachbit. But now i have to install manually when updating the bleachbit-bonus, also i am not sure if it is stable my system because of this error which i get from "software center" of Ubuntu 10.04 (which is full updated). Can someone help me about this issue?
(I asked to Bleachbit forums and they say that i have to ask it here.)
Thank you!

---

### Post by kema_u on 2010-09-18
Please someone help me ? :confused:

---

### Post by melkespreng on 2010-09-18
Thats because bleachbit-bonus is not in the repositories like the main program of bleachbit is. But if you got it working you did it right and the deb package you installed can be removed in the terminal/synaptic/software center.

---

### Post by kema_u on 2010-09-19
melkespreng thank for your interest. I know that i can delete my deb package after i want. But i dont know if it is stable or if i should to install to my ubuntu ? (i am able to do not install this package ofcourse but i need some directories to clean, i mean it is good for me to install this extra package).

---

### Post by gandaran on 2010-09-19
> **kema_u said:**
> melkespreng thank for your interest. I know that i can delete my deb package after i want. But i dont know if it is stable or if i should to install to my ubuntu ? (i am able to do not install this package ofcourse but i need some directories to clean, i mean it is good for me to install this extra package).
thats up to you to find out! if it works okay keep it, if it doesn't remove it!
my opinion is that you don't really need any cleaning up software, if you learn how to use synaptic package manager you will not need Bleachbit.
and a couple clean up commands too
```
sudo apt-get clean
sudo apt-get autoclean
```
Bleachbit for me is useless!

---

### Post by kema_u on 2010-09-19
Belahbit bit cleans many temp files from system. In additional we have this problem too : [http://ubuntuforums.org/showthread.php?t=1577295](http://ubuntuforums.org/showthread.php?t=1577295)

---

