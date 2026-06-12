---
title: "Printer driver fails and ruins my system."
date: 2010-10-27
forum: General Help
---

### Post by Cityscape on 2010-10-27
I am trying to get my Brother MFC 4800 printer driver installed but  every time it fails (details below). But the problem is that I cannot do any updates or open synaptic any more. Synaptic tells me "E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.  E: Internal error opening cache (1). Please report." Update Manager tells me "Software index is broken. It is impossible to install or remove any software. Please use the package manager Synaptic or run sudo apt-get install -f in a terminal to fix this issue at first." And I aldo have a warning icon on the right side of my taskbar. If I put my mouse over it it says "An error occurred, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Unkown Error:'<type'exceptions.systemError'> (E: the package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.) This usually means that your installed packages have unmet dependencies."

I've installed this driver on many computers but never had this problem. Please help.


```
adam@Compaq-PC:~/Programs$ dpkg  -i  --force-all mfc4800lpr-1.1.2-1.i386.deb
dpkg: operation requires read/write access to dpkg status area
adam@Compaq-PC:~/Programs$ sudo dpkg  -i  --force-all mfc4800lpr-1.1.2-1.i386.deb
(Reading database ... 78032 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc4800lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc4800lpr-1.1.2-1.i386.deb
```

---

### Post by sandyd on 2010-10-27
> **Cityscape said:**
> I am trying to get my Brother MFC 4800 printer driver installed but  every time it fails (details below). But the problem is that I cannot do any updates or open synaptic any more. Synaptic tells me "E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.  E: Internal error opening cache (1). Please report." Update Manager tells me "Software index is broken. It is impossible to install or remove any software. Please use the package manager Synaptic or run sudo apt-get install -f in a terminal to fix this issue at first." And I aldo have a warning icon on the right side of my taskbar. If I put my mouse over it it says "An error occurred, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Unkown Error:'<type'exceptions.systemError'> (E: the package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.) This usually means that your installed packages have unmet dependencies."

I've installed this driver on many computers but never had this problem. Please help.


```
adam@Compaq-PC:~/Programs$ dpkg  -i  --force-all mfc4800lpr-1.1.2-1.i386.deb
dpkg: operation requires read/write access to dpkg status area
adam@Compaq-PC:~/Programs$ sudo dpkg  -i  --force-all mfc4800lpr-1.1.2-1.i386.deb
(Reading database ... 78032 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc4800lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc4800lpr-1.1.2-1.i386.deb
```

```

sudo ln -s /etc/init.d/cpus /etc/init.d/lpd

```

---

### Post by Cityscape on 2010-10-27
```
ln: creating symbolic link `/etc/init.d/lpd': File exists
```

---

### Post by sandyd on 2010-10-27
> **Cityscape said:**
> ```
ln: creating symbolic link `/etc/init.d/lpd': File exists
```

weird. if lpd already exists, the deb should be able to find it.

---

### Post by Cityscape on 2010-10-27
> **sandyd said:**
> weird. if lpd already exists, the deb should be able to find it.
I did everything (the prerequisite steps) like I normally do. T forgot to mention that I'm using Lubuntu 10.10, and this printer has installed well on other computers running Ubuntu 10.10.

What should I try next?

---

### Post by cavalier911 on 2010-10-28
There is incorrect reference to the /etc/init.d/cups script earlier in this thread as "/etc/init.d/cpus" and on the brother solutions pre-requisite(3) "/etc/init.d/cupsys"
Successful test of valid lpd symlink:
```
rj@lubuntu:~$ sudo /etc/init.d/lpd restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
rj@lubuntu:~$ sudo /etc/init.d/lpd stop
 * Stopping Common Unix Printing System: cupsd                           [ OK ] 
rj@lubuntu:~$ sudo /etc/init.d/lpd start
 * Starting Common Unix Printing System: cupsd                           [ OK ] 
```
Dead links are red,valid links are blue in lxterminal.
Your blue lpd symbolic link will output:
```
rj@lubuntu:~$ ls -la /etc/init.d/lpd
lrwxrwxrwx 1 root root 16 2010-10-28 20:40 /etc/init.d/lpd -> /etc/init.d/cups

```
You have to delete a dead link:
```
rj@lubuntu:~$ sudo rm /etc/init.d/lpd
```
To make a correct link:
```
rj@lubuntu:~$ sudo ln -s /etc/init.d/cups /etc/init.d/lpd
```


There are other pre-requisites:
```
"mkdir /var/spool/lpd" is required if the folder does not exist.
```
No /var/spool/lpd on lubuntu 10.7

Once you get this working report what pre-requisites were required.

---

### Post by Vigh on 2010-10-31
I currently have the exact same problem I am trying a work around currently will let you know how it goes.

currently through terminal I have done-

sudo apt-get build-dep dpkg

dependencies didn't seem to be installed correctly for dpkg, hopefully this fixes the driver installation process

---

### Post by Vigh on 2010-10-31
purged everything, installed dpkg dependencies and reinstalled brother printer drivers, printer works perfectly now, hope it is the same issue with you and your problem is solved, regards

---

### Post by hic3456 on 2010-12-28
well, it's not as simple as all that...

the links are just fine: /etc/init/lpd points to the correct /etc/init.d/cups, however (I'm guessing because the authors of the service are trying to be smart) invoking directly: /etc/init.d/lpd causes the script to fail with an 'Unknown job':

```
marco@mordor:/tmp$ /etc/init.d/lpd start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service lpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start lpd
start: Unknown job: lpd

```

I am not quite sure how to fix this inside the CUPS wrapper or LPD driver from Brother, but I suspect Brother would need to fix it.

I also eventually managed to get the printer up and running, but having fiddled with CUPS (both in the web interface at [http://localhost:631](http://localhost:631) as well as with the simple GUI client in System > Administration > Printing) for quite some time, not quite sure what got it unstuck.

---

