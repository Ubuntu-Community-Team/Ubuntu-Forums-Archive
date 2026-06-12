---
title: "apt problem"
date: 2009-10-26
forum: General Help
---

### Post by Woody1987 on 2009-10-26
I am having a problem trying to upgrade ubuntu, when i do so i get the following error:

```
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `pulseaudio-module-x11' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I have tried the following commands but all to no avail:
sudo dpkg --configure -a 
sudo apt-get -f install
sudo dpkg --clear-avail
sudo dpkg-reconfigure -a

What else can i do?

---

### Post by phillw on 2009-10-26
This thread has some inform the matter.

[http://ubuntuforums.org/showthread.php?p=8159941](http://ubuntuforums.org/showthread.php?p=8159941)

Regards,

Phill.

---

### Post by Woody1987 on 2009-10-26
> 
This thread has some inform the matter.

[http://ubuntuforums.org/showthread.php?p=8159941](http://ubuntuforums.org/showthread.php?p=8159941)

Regards,

Phill.

That doesnt help, i dont have a sound problem, i cant upgrade my system.

---

### Post by freecru on 2009-10-26
from here: [http://newyork.ubuntuforums.org/showthread.php?t=1259371](http://newyork.ubuntuforums.org/showthread.php?t=1259371) and changed for your situation..

```
sudo mv /var/lib/dpkg/info/pulseaudio-module-x11.list /var/lib/dpkg/info/pulseaudio-module-x11.list.broke
sudo apt-get --reinstall install pulseaudio-module-x11

```

The OP in that thread said the machine required a reboot after the reinstall. Perhaps this will fix your issue?

---

### Post by Woody1987 on 2009-10-26
> from here: [http://newyork.ubuntuforums.org/show....php?t=1259371](http://newyork.ubuntuforums.org/show....php?t=1259371) and changed for your situation..

Code:

sudo mv /var/lib/dpkg/info/pulseaudio-module-x11.list /var/lib/dpkg/info/pulseaudio-module-x11.list.broke
sudo apt-get --reinstall install pulseaudio-module-x11

The OP in that thread said the machine required a reboot after the reinstall. Perhaps this will fix your issue?

Thanks that worked, i can now upgrade with one exception i now get this error:

```
matt@matt-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  jockey-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
21 not fully installed or removed.
Need to get 136kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get: 1 http://gb.archive.ubuntu.com karmic/main jockey-common 0.5.5-0ubuntu2 [136kB]
Fetched 136kB in 0s (245kB/s)     
(Reading database ... 10%
dpkg: warning: files list file for package `jockey-common' missing, assuming package has no files currently installed.
(Reading database ... 150191 files and directories currently installed.)
Preparing to replace jockey-common 0.5.5-0ubuntu1 (using .../jockey-common_0.5.5-0ubuntu2_all.deb) ...
pycentral: pycentral pkgremove: package jockey-common is not installed
pycentral pkgremove: package jockey-common is not installed
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package jockey-common is not installed
pycentral pkgremove: package jockey-common is not installed
dpkg: error processing /var/cache/apt/archives/jockey-common_0.5.5-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package jockey-common is not installed
pycentral pkginstall: package jockey-common is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/jockey-common_0.5.5-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Woody1987 on 2009-10-26
fixed, sudo apt-get -f install

---

