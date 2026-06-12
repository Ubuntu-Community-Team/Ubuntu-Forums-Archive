---
title: "need help in oracle installation"
date: 2011-05-09
forum: General Help
---

### Post by awaistoor on 2011-05-09
im using an old computer having 900 MHz processor, 512 MB RAM, and 20GB HDD. I want to install oracle on this computer. i tried to download oracle 9i but i think its obsellete now so couldnt find its setup for ubuntu on net. so now im trying to install oracle 10g on it but im having problem that my swap space isnt completing the minimum requirements to install oracle 10g. 

im receiving this error:

```

(Reading database ... 119507 files and directories currently installed.)
Unpacking oracle-xe-universal (from oracle-xe-universal_10.2.0.1-1.0_i386.deb) ...
This system does not meet the minimum requirements for swap space.  Based on
the amount of physical memory available on the system, Oracle Database 10g
Express Edition requires 992 MB of swap space. This system has 852 MB
of swap space.  Configure more swap space on the system and retry the installation.
dpkg: error processing oracle-xe-universal_10.2.0.1-1.0_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-xe-universal_10.2.0.1-1.0_i386.deb

```

so i need help either in downloading n installing the oracle 9i or solving this problem.\
your help will be appreciated

awaistoor

---

### Post by Buntumatic on 2011-05-09
Add a swap file to satisfy the requirement.

---

### Post by awaistoor on 2011-05-10
> **Buntumatic said:**
> Add a swap file to satisfy the requirement.

i have done that but still not worked .. any other idea ??

---

### Post by Habitual on 2011-05-10
...This system does not meet the minimum requirements for swap space.  Based on the amount of ***_physical memory_*** available on the system... yada yada yada.

Buy more RAM.

---

### Post by awaistoor on 2011-05-22
> **Habitual said:**
> ...This system does not meet the minimum requirements for swap space.  Based on the amount of ***_physical memory_*** available on the system... yada yada yada.

Buy more RAM.

lol .. well i have installed oracle on the same system (widout increasing RAM) :P but now the problem is to configure it .. im working on that :D

---

