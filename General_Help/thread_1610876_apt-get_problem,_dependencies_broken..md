---
title: "apt-get problem, dependencies broken."
date: 2010-11-01
forum: General Help
---

### Post by jodgi on 2010-11-01
System:
Ubuntu 8.04, 2.6.24-28-generic i686

During an upgrade routine a while ago the system froze, I do not know the details but the routine was interrupted. Now I can't make any upgrades. There seems to be some unmet dependencies which I don't know how to fix.

Here's a bit of apt-get output:
```

sudo apt-get check:

Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xulrunner-1.9.2-gnome-support: Depends: xulrunner-1.9.2 (= 1.9.2.9+build1+nobinonly-0ubuntu0.8.04.1) but 1.9.2.8+build1+nobinonly-0ubuntu0.8.04.1 is installed

sudo apt-get -f install:

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  xulrunner-1.9.2 xulrunner-1.9.2-gnome-support
The following packages will be upgraded:
  xulrunner-1.9.2 xulrunner-1.9.2-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
2 not fully installed or removed.
Need to get 0B/9800kB of archives.
After this operation, 57.3kB of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ... dpkg: error processing /var/cache/apt/archives/xulrunner-1.9.2-gnome-support_1.9.2.12+build1+nobinonly-0ubuntu0.8.04.1_i386.deb (--unpack):
 files list file for package `firefox' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9.2-gnome-support_1.9.2.12+build1+nobinonly-0ubuntu0.8.04.1_i386.deb
Processing was halted because there were too many errors.
```

I've tried to manually purge xulrunner and firefox, clean, autoclean but it all stops just like listed in the output quoted over.

I'm guessing it has to do with the > files list file for package `firefox' contains empty filename I do not know fully what this means or how to fix it.

Any ideas?

---

### Post by MooPi on 2010-11-01
Try ```
dpkg --configure -a
``` This will attempt to install partially install packages. Just to check have you run ```
sudo apt-get update
```

---

### Post by jodgi on 2010-11-02
```
sudo dpkg --configure -a
[sudo] password for xxxxxx: 
dpkg: dependency problems prevent configuration of xulrunner-1.9.2-gnome-support:
 xulrunner-1.9.2-gnome-support depends on xulrunner-1.9.2 (= 1.9.2.9+build1+nobinonly-0ubuntu0.8.04.1); however:
  Package xulrunner-1.9.2 is not installed.
dpkg: error processing xulrunner-1.9.2-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.2-gnome-support
```

The message above is spit out instantly

And then apt-get update finishes without any error messages.

If some apt-get logfiles have been wiped or corrupted, is there a way to regenerate and fix? I'm thinking of the "firefox" error message qouted in my first post.

---

