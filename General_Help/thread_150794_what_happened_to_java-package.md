---
title: "what happened to java-package ?"
date: 2006-03-26
forum: General Help
---

### Post by spearfish on 2006-03-26
Hi,

I'm trying to do the following command and it's not working:

sudo apt-get install fakeroot java-package java-common

My system says that it can not find anything called "java-package".

I'm trying to install java on my system and I'm following someone's online instructions.  Can anyone offer a suggestion?

thanks!

---

### Post by Xian on 2006-03-26
Read the wiki entry on how to get [JAVA](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport#head-68565ae07a003332e82c9f23706638777396c249) and [Adding Repos](https://wiki.ubuntu.com/AddingRepositoriesHowto).

$ sudo apt-get install j2re1.4

---

### Post by spearfish on 2006-03-26
Hi Xian,

I looked at the wiki on Getting Java and they had the same directions that I was following.  However, there was one important thing that I was missing.  The page says:

  sudo apt-get install fakeroot java-package java-common

"If you get an error when installing java-package, you need to enable the multiverse repository (see AddingRepositoriesHowto). "

Ah ha!  If other people have this problem, here is the solution.  I went to Synaptic Package Manager, clicked on Settings, Repositories, then click on ADD +
From there, select UBUNTU 5.10 "Breezy Badger" and check the box that says:
Non-Free (Multiverse)

After doing that, I did the following successfully:

user@system:~$ sudo apt-get install java-package java-common
Password:
Reading package lists... Done
Building dependency tree... Done
java-common is already the newest version.
The following NEW packages will be installed:
  java-package
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.3kB of archives.
After unpacking 315kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse java-package 0.26 [21.3kB]
Fetched 21.3kB in 0s (78.4kB/s)

Preconfiguring packages ...
Selecting previously deselected package java-package.
(Reading database ... 64124 files and directories currently installed.)
Unpacking java-package (from .../java-package_0.26_all.deb) ...
Setting up java-package (0.26) ...
user@system:~$

Seems to have gone ok.  Thanks for the assistance. :)

---

