---
title: "update error: firefox-4.0-core plz help"
date: 2010-12-09
forum: General Help
---

### Post by Unix3r on 2010-12-09
hello
when i try to update ubuntu
i got this message after it says update fail

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 177055 files and directories currently installed.) 
Preparing to replace thunderbird 3.1.8~hg20101203r5898+nobinonly-0ubuntu2~umd2~maverick (using .../thunderbird_3.1.8~hg20101208r5906+nobinonly-0ubuntu1~umd1~maverick_i386.deb) ... 
Unpacking replacement thunderbird ... 
Preparing to replace xulrunner-1.9.2 1.9.2.14~hg20101206r34804+nobinonly-0ubuntu1~umd1~maverick (using .../xulrunner-1.9.2_1.9.2.14~hg20101208r34808+nobinonly-0ubuntu1~umd1~maverick_i386.deb) ... 
Unpacking replacement xulrunner-1.9.2 ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up firefox-4.0-core (4.0~b8~hg20101207r58752+nobinonly-0ubuntu1~umd1~maverick) ... 
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist. 
dpkg: error processing firefox-4.0-core (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up thunderbird (3.1.8~hg20101208r5906+nobinonly-0ubuntu1~umd1~maverick) ... 
Setting up xulrunner-1.9.2 (1.9.2.14~hg20101208r34808+nobinonly-0ubuntu1~umd1~maverick) ... 
update-alternatives: using /usr/bin/xulrunner-1.9.2 to provide /usr/bin/xulrunner (xulrunner) in auto mode. 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 firefox-4.0-core 
Setting up firefox-4.0-core (4.0~b8~hg20101207r58752+nobinonly-0ubuntu1~umd1~maverick) ... 
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist. 
dpkg: error processing firefox-4.0-core (--configure): 
 subprocess installed post-installation script returned error exit status 2

Anybody know how to fix this problem?

---

### Post by Unix3r on 2010-12-09
nobody know how to fix this issue?

---

### Post by pabjvar on 2010-12-09
I'm having the same problem and have the same inquiries... this bug is not letting me install anything in my computer neither letting me open folder in the homefolder from the places tap...

---

### Post by WorMzy on 2010-12-09
I assume you have added a third party repository to get firefox 4, because the latest version in the official repos, for Maverick, is 3.6.12. Try reinstalling that version with
```
sudo apt-get install firefox=3.6.12+build1+nobinonly-0ubuntu0.10.10.1
```

---

### Post by pabjvar on 2010-12-09
This is what I got: 

> :~$ sudo apt-get install firefox=3.6.12+buildl+nobinonly-0ubuntu0.10.10.1
[sudo] password for pablo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '3.6.12+buildl+nobinonly-0ubuntu0.10.10.1' for 'firefox' was not found


I think I want to eliminate the firefox 4.0 core and maybe the PPA too...
and just have the normal firefox on...

the thing is that it is preventing me from installing any update correctly and it is just causing corrupted files... I think...

---

### Post by WorMzy on 2010-12-09
You used a lower case L instead of the number 1 here:

```
sudo apt-get install firefox=3.6.12+build**_l_**+nobinonly-0ubuntu0.10.10.1
```

It's easier if you just copy and paste the command. ;)

You can disable (or remove) the PPA by opening your software sources. Unfortunately, I believe the Software Sources menu entry has been removed from Maverick, so you have to open Synaptic to get to it.

System -> Administration -> Synaptic Package Manager
 -> Settings -> Repositories -> Other Software

After you've disabled/removed the offending repository, run
```
sudo apt-get update
sudo apt-get autoclean
```

---

