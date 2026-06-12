---
title: "preload"
date: 2011-05-10
forum: General Help
---

### Post by david sousa on 2011-05-10
Hi,

I've started using preload some weeks ago. Now i want to turn it off but i don't know how. I've tried to uninstall preload but it still loads my programs when computer starts.

How do I stop that? (i'm using xubuntu)

Thanks

David

---

### Post by TheNerdAL on 2011-05-10
Did you try restarting after you uninstalled?

---

### Post by Toz on 2011-05-10
The package preload creates startup scripts in /etc/init.d. To properly uninstall preload, you should "purge' it:```
sudo apt-get purge preload
```
However, if you have already removed it, you won't be able to run the purge command. Since preload is a simple package without any dependencies (on my system anyways), you can fix this by reinstalling it then purging it.

Open up a command terminal and type in:```
sudo apt-get install preload
``` (you will be asked to enter your password). 

Once it is installed, run the following command to purge it:```
sudo apt-get purge preload
```

---

### Post by david sousa on 2011-05-21
Thanks!

---

