---
title: "How to install fglrx graphics driver from command line?"
date: 2011-06-07
forum: General Help
---

### Post by zcacogp on 2011-06-07
Chaps, 

Cutting a long story short (my machine won't allow me to login without the proprietary fglrx driver installed), how do you install the fglrx driver in Natty, from the console? 

The following commands have been suggested (many thanks to coffeecat on here for his help), but haven't worked: 

```

apt-get update
apt-get install fglrx fglrx-amdcccle fglrx-dev

```

Does anyone else have any suggestions? 

Thanks, in advance, for any help anyone can offer. (It will hopefully save me from having to re-install, which seems to be about my only other option.) 


Oli. 

P.S. For more details of the background to this saga, see here: 

[http://ubuntuforums.org/showthread.php?p=10914117&posted=1#post10914117](http://ubuntuforums.org/showthread.php?p=10914117&posted=1#post10914117)

---

### Post by zcacogp on 2011-06-08
OK, coming back to this one as the problem is now solved ... 

I discovered that if you choose "recovery mode" at GRUB, one of the options is to start in low-graphics mode. This allows you into the system, and from there you can install the graphics driver normally. 

Hope this is helpful to someone else, sometime in the future ... !


Oli.

---

### Post by Mark Phelps on 2011-06-08
You could try the commands in the first part of the link below:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

