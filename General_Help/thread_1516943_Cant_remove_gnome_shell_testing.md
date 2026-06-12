---
title: "Cant remove gnome shell testing"
date: 2010-06-24
forum: General Help
---

### Post by automotive on 2010-06-24
I tried gnome shell (PPA), but failed to remove it. And I cant install other packages now. Update manager cant works properly as well. I got this in terminal:
```
hjj@ubuntu:~$ sudo apt-get remove gnome-shell
[sudo] password for hjj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-shell
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,245kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 156089 files and directories currently installed.)
Removing gnome-shell ...
/var/lib/dpkg/info/gnome-shell.postrm: 10: glib-compile-schemas: not found
dpkg: error processing gnome-shell (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It shows that the package of gnome-shell is broken in Synaptic Package Manager, and I cant fix it or remove it. It shows like this:
[ATTACH]161416[/ATTACH]
[ATTACH]161417[/ATTACH]
How can I fix it? Please help

---

### Post by automotive on 2010-06-27
Problem was solved finally, this post helped me:[http://ubuntuforums.org/showthread.php?t=1359853&highlight=subprocess+installed+post-removal+script+returned+error+exit+status+127](http://ubuntuforums.org/showthread.php?t=1359853&highlight=subprocess+installed+post-removal+script+returned+error+exit+status+127)

---

