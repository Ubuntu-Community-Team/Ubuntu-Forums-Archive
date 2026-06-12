---
title: "package manager and openoffice.org-emailmerge"
date: 2011-03-03
forum: General Help
---

### Post by lecote on 2011-03-03
I am new to Ubuntu, but have been using it (and falling in love with it) for the past month. However, I have hit a snag: I have been trying to install a new program, but cannot due to an issue with openoffice.org-emailmerge. Whenever I try to install something, apt-get freezes when it tries to update because it cannot update emailmerge. After a bit of googling to try to fix it, I decided just to remove the program. However, but I get the following message (if I use Synaptic, it freezes): 

> sudo apt-get remove openoffice.org-emailmerge 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-24-generic linux-headers-2.6.35-24
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openoffice.org-emailmerge
0 upgraded, 0 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing openoffice.org-emailmerge (--remove):
[B] Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/B]
Errors were encountered while processing:
 openoffice.org-emailmerge
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't do work until I install R and I can't install anything until this is fixed! HELP!

---

### Post by sikander3786 on 2011-03-05
Hi.

Did you try reinstalling the package as is suggested. Please post the output of this command.

```
sudo apt-get install --reinstall openoffice.org-emailmerge
```

---

