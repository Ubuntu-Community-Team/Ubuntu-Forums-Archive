---
title: "i have this issue"
date: 2010-01-20
forum: General Help
---

### Post by freefixkorma on 2010-01-20
hi guys i am sorry if i did not post this in the correct place but here it goes i am trying to download virtual box and pops up window that said there is another program similar and it cant download it ,so i guess was wine so i try to delete wine and there is message pops up here is will appreciate any guide and how to thanks 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by doas777 on 2010-01-20
ok, in the case of the message about having more than one application, is it telling you that it cannot lock the database becase it is in use? if so, you may have synaptic, or software center open at the same time. only one application can install/uninstall apps at a time, so you can't have both synaptic open and do and apt-get install. 

for your dpkg error, you will need to open a terminal and enter:
```
sudo dpkg --configure -a
```

---

### Post by fooman on 2010-01-20
open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo dpkg --configure -a
```

then press enter,  followed by your password when prompted.

then in the same terminal,  run the following:

```
sudo apt-get update
```

see if that helps.

---

### Post by synapsys on 2010-01-20
Wine shouldn't be conflicting with virtualbox for any reason. First of all you need to open a terminal Applications >> Accessories >> Terminal and type:

```
sudo dpkg --configure -a
```

And then we can figure out why you are getting this error. Do you perhaps already have a version of virtualbox installed?

---

### Post by freefixkorma on 2010-01-22
hi sir i did the code that you told me and i get this window
Unable to find a precompiled module for the current kernel!               &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Without a suitable kernel module you will not be able to start any VMs.   &#9474; 
 &#9474; It is strongly recommended to compile a kernel module now. The kernel     &#9474; 
 &#9474; headers and the tools to build kernel modules (gcc, make, binutils, ...)  &#9474; 
 &#9474; are required. However if you know that a suitable kernel module already   &#9474; 
 &#9474; exists at another location, you might want to override the default by     &#9474; 
 &#9474; setting KDIR=<full_path_to_vboxdrv_module> in /etc/default/virtualbox.    &#9474; 
 &#9474; The compilation can also be done later by executing                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;   /etc/init.d/vboxdrv setup                                               &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; as root.

---

