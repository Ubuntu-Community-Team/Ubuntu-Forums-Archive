---
title: "Please help"
date: 2009-08-06
forum: General Help
---

### Post by danielshewchuk on 2009-08-06
**Re: Please help** 			
 			 			 		   		 		 		From trying to install flashplugin-nonfree in terminal i get this message

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Anxious Nut on 2009-08-06
the error says that the package manager is being used at that time

the package manager -using synaptic or add/remove or apt-get or whatever- should be used once at a time

so make sure that only one program is installing or in a process

---

### Post by warp99 on 2009-08-06
Another application is using dpkg such as Synaptic or Gdebi. Make sure all of those applications are closed. If they are closed and you still get the error remove the lock:

```
sudo rm -f /var/lib/dpkg/lock
```

---

### Post by danielshewchuk on 2009-08-12
After i remove the lock then what do i do??? I have been trying everything and it still seems to not work.

---

