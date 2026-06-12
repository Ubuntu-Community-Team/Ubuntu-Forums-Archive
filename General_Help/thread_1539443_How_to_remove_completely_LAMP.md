---
title: "How to remove completely LAMP?"
date: 2010-07-26
forum: General Help
---

### Post by MicroBoy on 2010-07-26
How to remove completely LAMP, I had some problems after I made some changes, now I want to remove everything that has to do with LAMP and install again from the beginning, If I use "apt-get remove" and then when I try to install it has the packages somewhere it just selects, it does not download from Internet. I want it to be downloaded again from Internet like the first time and not just to be selected from the PC.

---

### Post by rubylaser on 2010-07-26
```
sudo apt-get remove --purge apache2 php5 mysql-server-5.0 phpmyadmin
```

This will completely remove a package.  You still won't have to re-download the packages though, unless changes have been made to the repository.  This will just remove the LAMP stack, and associated config files.

---

### Post by MicroBoy on 2010-07-26
I did it and installed again but I still have that problem:S the problem is with phpmyadmin, and during the way to fix it I messed up more, is that any chance to completely remove it and than to be downloaded like the first time, or I just need to install Ubuntu from the beginning?

p.s. there has to be a config file that does not remove and that cause all the problems:S

---

### Post by rubylaser on 2010-07-27
phpmyadmin is just a series of directories.  Just re-run the 
```
sudo apt-get remove --purge phpmyadmin
``` 

This will literally **completely** remove phpmyadmin from your machine.
```
sudo find -L / -name "phpmyadmin*" -print0 |xargs -0 -r rm
```

then from a terminal run this...
```
find / -name "phpmyadmin*" 
```
If it doesn't find anything, phpmyadmin does not exist on your system anymore.  Then you could do this...
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install phpmyadmin
```

If it doesn't work after this, phpmyadmin isn't causing your problem, it's something else.

---

