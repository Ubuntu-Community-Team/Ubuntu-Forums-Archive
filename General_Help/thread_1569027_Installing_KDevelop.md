---
title: "Installing KDevelop"
date: 2010-09-06
forum: General Help
---

### Post by doriad on 2010-09-06
I am trying to install KDevelop. Can anyone see what is going wrong?

```

doriad@davidlaptop:~$ sudo apt-get install kdevelop
[sudo] password for doriad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdevelop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdevplatform1-libs
E: Package kdevelop has no installation candidate
doriad@davidlaptop:~$ sudo apt-get install kdevplat*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting kdevplatform-dbg for regex 'kdevplat*'
Note, selecting kdevplatform-dev for regex 'kdevplat*'
Note, selecting kdevplatform1-libs for regex 'kdevplat*'
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
doriad@davidlaptop:~$ kdevelop&
[1] 20107
doriad@davidlaptop:~$ No command 'kdevelop' found, did you mean:
 Command 'qdevelop' from package 'qdevelop' (universe)
kdevelop: command not found


```

Thanks,

David

---

### Post by GregBrannon on 2010-09-06
What OS (as much detail as possible) are you trying to install it to?

---

### Post by an0dos on 2010-09-06
Are you using 10.04? If so, you have to enable the 'backports' repository. You can modify your repositories through the synaptic package manager. Once you have enabled said repository, refresh the package list and search for kdevelop through synaptic.

---

### Post by doriad on 2010-09-06
@Greg - it is 10.04 - sorry, I should have specified.

@an0dos - Thanks a lot, that did the trick.

David

---

