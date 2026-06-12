---
title: "Running out of Space"
date: 2009-11-28
forum: General Help
---

### Post by banerjeerupak on 2009-11-28
Hi, 

I'm running out of space in my primary drive. I would like to free up some space. Is it possible to remove the downloaded update files that are stored somewhere. I mean if the files are no longer needed. Can you update files be deleted?

Thanks

Rupak

---

### Post by XCan on 2009-11-28
```
 sudo apt-get autoremove
sudo apt-get autoclean 
``` comes to mind. In addition, take a look at the disk usage analyzer in Applications if you wnat to track down large files. :)

---

### Post by ibuclaw on 2009-11-28
As well as the above:
```
sudo apt-get clean
```
Performs a "total" clean of all downloaded packages.

You can also install two useful cleaning packages.
```
sudo apt-get install deborphan localepurge
```
For localepurge, set the locale as **en** and whatever language you are comfortable in.

Then run:
```
sudo localepurge
```
to clean out all foreign manpages / other. There is nothing else to do for that, as localepurge hooks into the dpkg installation routine and runs every time you install/upgrade a package.


For deborphan, run:
```
sudo aptitude purge $(deborphan)
```
You can also purge any residual data too:
```
sudo aptitude purge $(dpkg -l | awk '/^rc/ { print $2 }')
```

Lastly, Ubuntu now has a GUI cleaner call **Janitor** in the Administration part of the System menu.

Regards
Iain

---

### Post by X1R1 on 2009-11-28
To wipe out space from my drive I use a neat script tha I found [here]("http://www.opendesktop.org/content/download.php?content=71529&id=1&tan=89063233")

As with any script, give it execute permisions:

> chmod -c 744 71529-ubucleaner.sh

and execute with:

> sudo ./71529-ubucleaner.sh

Remember to do this commands on the same folder that you downloaded the script. This script does this:

-Cleans Apt cache
-Removes old kernels
-Removes old configuration files of uninstalled packages
-Empties all trashes

I have been using this for a while now and its very safe and usefull.
Hope you like it

---

### Post by banerjeerupak on 2010-05-07
Thank You. 

Problem solved.

---

