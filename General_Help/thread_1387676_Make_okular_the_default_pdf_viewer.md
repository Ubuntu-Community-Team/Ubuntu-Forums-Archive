---
title: "Make okular the default pdf viewer"
date: 2010-01-22
forum: General Help
---

### Post by Despot Despondency on 2010-01-22
Hi,

Simple question, how do I make okular my default pdf viewer? At the moment it is evince but I want to swap.

Also is it possible to remove evince? When I run 

```

sudo aptitude remove evince

```

I get 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  evince 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 5,825kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: evince but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Score is 119

Accept this solution? [Y/n/q/?] 

```

I don't want to break anything. TAI

---

### Post by sisco311 on 2010-01-22
You can right click on a pdf file -> Properties -> Open With tab and select your preferred application to open pdf files. The changes will apply to all the pdf files.


Before you remove evince, try to fix the broken package:
```
sudo apt-get install -f
```

ubuntu-desktop is a meta package, it's safe to remove it.
[uhelp]community/MetaPackages[/uhelp]

---

### Post by Despot Despondency on 2010-01-22
Thanks, I thought it'd be something simple like that.:)

---

