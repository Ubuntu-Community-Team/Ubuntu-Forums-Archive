---
title: "Brocken Package System"
date: 2012-08-11
forum: General Help
---

### Post by Gingalone on 2012-08-11
I upgraded to Precise 12.04 (clean install) one month ago and this morning (after un update) something went wrong: when I start the Ubuntu Software Center I get a warning about the package catalog (see screenshot1) and when I click on Repair I get an error response (Screenshot2 (imposible to enlarge the window!)).

If I start the Update Manager I get the usual window (Screenshot3) and then, on install, another error response window (Screenshot4) which says the package system is brocken because it is not installed the package that Update Manager was going to install!!! VERY confusing!

What about?
Thanks for any help!

---

### Post by TheFu on 2012-08-11
No need to panic yet.  Try again tomorrow and again on Monday. If it continues, you'll want to drop to a terminal, try the update again and post the exact errors here.

Waiting a few days gives the developer time to correct any issues they may have missed or for a corrupt package to be discovered and fixed, that's all.

---

### Post by Gingalone on 2012-08-13
Sorry I had forgotten the response of the suggested command:```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-29-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-29-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/985 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 216808 files and directories currently installed.)
Unpacking linux-headers-3.2.0-29-generic-pae (from .../linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by plucky on 2012-08-13
> Unpacking linux-headers-3.2.0-29-generic-pae (from .../linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'

You probably need to download the package again as there seems to be a problem with the package.

Run from a terminal ```
sudo apt-get clean
``` which will remove all the packages in /var/cache/apt/archives/ directory and then run ```
sudo apt-get install -f
``` again to try to fix the problem.

If you don't want to delete all the packages in the /var/cache/apt/archives/ directory,you could try to just delete the package with ```
sudo rm /var/cache/apt/archive/linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb
``` and then run the apt-get install -f command again.

Good luck

---

### Post by Gingalone on 2012-08-18
> **plucky said:**
> you could try to just delete the package with ```
sudo rm /var/cache/apt/archive/linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb
```
Good luck

done that, no luck. Got:```
rm: cannot remove `/var/cache/apt/archive/linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb': No such file or directory
```

---

### Post by plucky on 2012-08-18
> **Gingalone said:**
> done that, no luck. Got:```
rm: cannot remove `/var/cache/apt/archive/linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb': No such file or directory
```

Did you run ```
sudo apt-get clean
```?

If you did then that does the same thing as the remove command,but for all the files in the directory.

What happens if you run ```
sudo apt-get install -f
```

---

### Post by Gingalone on 2012-08-21
It worked!
Thank you plucky! ):P

---

