---
title: "How to fix broken package"
date: 2010-07-15
forum: General Help
---

### Post by labtek on 2010-07-15
Hello to the group and good day.

I've been running Ubuntu 8.04 quite happily for almost 2 years now.  During a recent update,a message came on the screen that I had 3 broken packages.

I used the filter in Synaptic to find them. The search indicated that the following packages were broken

sun-java 6-bin
sun-java 6-jre
sun-java 6- plugin

When I marked sun-java 6-bin for upgrade, this message appeared...


E: /var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.8.04.1_i386.deb: 
corrupted filesystem tarfile - corrupted package archive[/I]

I was wondering if there would be any value to uninstall sun-java6-bin and re-install it from the repositories.

Thanks for any thoughts.

---

### Post by MooPi on 2010-07-15
Before you uninstall try this. Open a terminal and type ```
sudo apt-get autoremove
``````
sudo apt-get autoclean
``````
sudo apt-get update
``` then ```
sudo apt-get upgrade
```Hopefully this will clean and remove obsolete archives.

---

### Post by stoneage on 2010-07-15
The error message suggests the package archive is corrupt:- 
/var/cache/apt/archives/sun-java6-bin_6.20dlj-0ubuntu1.8.04.1_i386.deb

If you remove those files and then update, synaptic will download them afresh.

---

### Post by labtek on 2010-07-15
Hi again and thanks for the reply.

This is the reply from the command sudo apt-get autoremove


labtek@diana-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6.20dlj-0ubuntu1.8.04) but 6.20dlj-0ubuntu1.8.04.1 is installed
  sun-java6-jre: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.8.04.1) but 6.20dlj-0ubuntu1.8.04 is installed or
                          ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.8.04.1) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.8.04.1) but 6.20dlj-0ubuntu1.8.04 is installed
E: Unmet dependencies. Try using -f.
labtek@diana-desktop:~$ 

I guess I'm not sure what "unmet dependencies" mean- have I run out of options?

Thanks

---

### Post by labtek on 2010-07-15
Thanks. I uninstalled all 3 packages and re-installed from Synaptic.

The error messages have disappeared.

---

### Post by barrymmm on 2010-09-12
I had a similar problem. After a routine package update firefox died on me and when I tried to open it up I got this message:

XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 31, Column 1:<window id="main-window"
^

After tryin to reinstall the packages in Synaptic I got this error message:

E: /var/cache/apt/archives/firefox_3.6.9+build1+nobinonly-0ubuntu0.9.10.2_i386.deb: corrupted filesystem tarfile - corrupted package archive

I read this thread and tried deleting 'firefox_3.6.9+build1+nobinonly-0ubuntu0.9.10.2_i386.deb' in the console but it wouldn't allow it so:

sudo rm firefox_3.6.9+build1+nobinonly-0ubuntu0.9.10.2_i386.deb

then standard package update did the trick nicely.

Thanks lads - I'm a total novice but you pointed me in the right direction :D

---

