---
title: "Broken packages"
date: 2012-04-12
forum: General Help
---

### Post by dh04000 on 2012-04-12
No matter what I do, I can't seem to fix this. Can someone help me please? I can't install anything or remove anything now. I'm running Ubuntu 12.04 64bit.


user@user-Aspire-4830TG:~$ sudo apt-get -f install
[sudo] password for devin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libbabl-0.0-0 libgegl-0.0-0 libgtkspell0 liblaunchpad-integration1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openjdk-6-jre
The following packages will be upgraded:
  openjdk-6-jre
1 upgraded, 0 newly installed, 0 to remove and 119 not upgraded.
1 not fully installed or removed.
Need to get 0 B/232 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 282429 files and directories currently installed.)
Preparing to replace openjdk-6-jre 6b24-1.11.1-3ubuntu3 (using .../openjdk-6-jre_6b24-1.11.1-4ubuntu1_amd64.deb) ...
Unpacking replacement openjdk-6-jre ...
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre_6b24-1.11.1-4ubuntu1_amd64.deb (--unpack):
 './usr/share/applications/openjdk-6-policytool.desktop' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre_6b24-1.11.1-4ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
devin@devin-Aspire-4830TG:~$

---

### Post by kc1di on 2012-04-12
Try this in a terminal.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by dh04000 on 2012-04-12
> **kc1di said:**
> Try this in a terminal.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```


I did this pair of commands, followed by a sudo apt-get upgrade

Which told me to do another sudo apt-get -f install


Same result, its still broken.


result in txt file at link.

[http://ubuntuone.com/0VHgawEadzLSlWNefl121V](http://ubuntuone.com/0VHgawEadzLSlWNefl121V)


EDIT: I don't have an ppa's install but one for Gimp 2.8, one for ubuntu tweak, mendeley, and bumblebee. None that affects java versions.

---

### Post by roelforg on 2012-04-12
Dude, your username is still visible in the sudo pass prompt

```

cd ~
sudo mv /usr/share/applications/openjdk-6-policytool.desktop .
sudo apt-get install -f

```

---

### Post by dh04000 on 2012-04-12
> **roelforg said:**
> Dude, your username is still visible in the sudo pass prompt

```

cd ~
sudo mv /usr/share/applications/openjdk-6-policytool.desktop .
sudo apt-get install -f

```


I changed that user name to user. Thanks for the heads up.


Also that code seemed to work. Its upgrading normally now. 

Thank you! :D

---

### Post by claracc on 2012-04-13
If you have solved your problem, please mark the thread as solved with thread tools in the upper right of the page. Only you can do this.

---

### Post by chugtairizwan on 2012-04-13
you guys are the source of information to me, i have read all the comments which are posted by you people, just keep it up guys.

---

### Post by roelforg on 2012-04-13
> **dh04000 said:**
> I changed that user name to user. Thanks for the heads up.
 
 
Also that code seemed to work. Its upgrading normally now. 
 
Thank you! :D
 
For the people curious to why it works:
dpkg (the backend for apt-get and other pkgmgrs) complains a file already exists,
it's only a shortcut but still a file.
So we move it to your home dir,
the new shortcut gets installed and dpkg stops complaining whilst not losing the old file.

---

### Post by mhgsys on 2012-04-13
not that I see the direct stress with it... but erh...


Your username is still there at the bottom of your first post mr D

---

### Post by dh04000 on 2012-04-13
Thread marked as solved.

I took the txt file down, no need to keep sharing it.


Thanks again for the help! I couldn't install or remove anything, so this really saved my tuckus. Thank you! :-D

---

