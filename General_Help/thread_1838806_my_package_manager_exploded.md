---
title: "my package manager exploded"
date: 2011-09-04
forum: General Help
---

### Post by cheesekiller on 2011-09-04
I installed Platinum Arts Sandbox Gamemaker   from the Ubuntu Software Center and it caused my dpkg (i think it is) to have errors.   Now when i go to install ANYTHING, remove ANYTHING, or update AT ALL, it goes ahead and removes, installs, updates but it gives me an error code ```
installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package p7zip-full.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 279462 files and directories currently installed.)
Unpacking p7zip-full (from .../p7zip-full_9.04~dfsg.1-1_amd64.deb) ...
Setting up man-db (2.5.9-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up acroread (9.4.2-0natty1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing acroread (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up p7zip-full (9.04~dfsg.1-1) ...
Errors were encountered while processing:
 man-db
 acroread
Setting up man-db (2.5.9-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up acroread (9.4.2-0natty1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing acroread (--configure):
 subprocess installed post-installation script returned error exit status 1

``` 

That is from me attempting to install 7zip (just as an example so i could copy the code)   

it does that whenever i do ANYTHING, it still installs,removes,updates but it still gives me the error and its rly rly annoying, sometimes dpkg locks up and i have to kill process

---

### Post by brucehohl on 2011-09-04
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

Suggest you reboot to make sure any 'orphaned' processes are terminated.

---

### Post by cheesekiller on 2011-09-05
i have rebooted a bunch of times.  someone else on the software center posted a review and it appears he had the same problem, so this leads me to believe 100% that it was this program especially since this only started after i installed it.

---

### Post by Tanasqui on 2011-09-09
I deselected the first entry in update manager, assumeing it was the culprit. After this, all other packages installed correctly. Restart was required then the previously deselected package was installed correctly.

---

### Post by cheesekiller on 2011-09-10
"cheesekiller likes this"    what there wasnt a like button

---

