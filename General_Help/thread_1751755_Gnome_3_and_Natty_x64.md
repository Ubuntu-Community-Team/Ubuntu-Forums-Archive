---
title: "Gnome 3 and Natty x64"
date: 2011-05-07
forum: General Help
---

### Post by JoshXT on 2011-05-07
Having a problem getting the gnome-themes-standard installed..

```
josh@Josh-Ubuntu:~$ sudo apt-get install gnome-themes-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-themes-standard
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0 B/977 kB of archives.
After this operation, 6058 kB of additional disk space will be used.
(Reading database ... 149946 files and directories currently installed.)
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.0.0-2~natty1_amd64.deb) ...
```

I just keep getting the same thing, even read a page telling me to run:
sudo apt-get remove gnome-accessibility-themes

Then to try to installing the gnome-themes-standard, it didn't work.

```
josh@Josh-Ubuntu:~$ sudo apt-get remove gnome-accessibility-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell : Depends: gnome-themes-standard (>= 2.91) but it is not going to be installed
```

Seems like I can't get one without getting rid of the other, and can't get rid of the other because of the other one.. I tried running apt-get -f install and it just threw the same errors at me..

So any help here would be greatly appreciated, I'm simply at a loss trying to figure this out.

---

