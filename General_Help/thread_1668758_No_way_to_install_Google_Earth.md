---
title: "No way to install Google Earth"
date: 2011-01-16
forum: General Help
---

### Post by rva1945 on 2011-01-16
I tried many times to no avail.

Maybe the problem is that I can't uninstall it, how to do it?

I had the previous version and the problems begen when I tried to upgrade to the latest version.

---

### Post by rva1945 on 2011-01-16
I managed to uninstall it, then downloaded and installed the package form googleearth.com, after the process finishes, a message says that the same version is already installed 

?

robert@rvasystem:~$ sudo apt-get remove googleearth
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package googleearth is not installed, so not removed**
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.
robert@rvasystem:~$ 

But it's still there: ApplicationsInternet/Google Earth, of course it doesn't lunch.

---

### Post by wilee-nilee on 2011-01-16
Run this command.
```
sudo apt-get install lsb-core
```
From this link, post #2.
[http://ubuntuforums.org/showthread.php?t=1634659](http://ubuntuforums.org/showthread.php?t=1634659)

---

### Post by jcolyn on 2011-01-16
Here ya go...

If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

---

### Post by rva1945 on 2011-01-16
> **jcolyn said:**
> Here ya go...

If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

THANKS MAN, I followed your steps, and now it works!!

The only small problem is that the old Application/Internet/Google Earth option still remains, so I have two now, I wonder whether I can delete one without affecting the other.

---

