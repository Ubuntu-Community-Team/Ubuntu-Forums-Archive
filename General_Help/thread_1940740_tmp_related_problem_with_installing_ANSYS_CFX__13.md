---
title: "/tmp related problem with installing ANSYS CFX  13"
date: 2012-03-14
forum: General Help
---

### Post by Nienna London on 2012-03-14
Hello,

I am trying to install ANSYS CFX v13 in a linux virtual machine (ubuntu-64 guest / windows 7 host). When I begin the installation process I get this error:

> username-VirtualBox:~/ANSYS13_Linux64/CFXinstallation$ ./INSTALL

copying necessary files to /tmp/ans_install_tmp2274/
 Executing /tmp/ans_install_tmp2274/instcore
/tmp/ans_install_tmp2274/INSTALL: 316: /tmp/ans_install_tmp2274/instcore: not foundI tried again as root and still got the same error. The /tmp folder seems to have enough space available.

Any help explained in simple terms (I am not very familiar with linux) will be much appreciated. :)

---

### Post by dcstar on 2012-03-15
> **Nienna London said:**
> Hello,

I am trying to install ANSYS CFX v13 in a linux virtual machine (ubuntu-64 guest / windows 7 host). When I begin the installation process I get this error:

I tried again as root and still got the same error. The /tmp folder seems to have enough space available.

Any help explained in simple terms (I am not very familiar with linux) will be much appreciated. :)

```
man sudo
```

---

### Post by Nienna London on 2012-03-16
Hi David,

Thank you, but it doesn't seem to be a permissions problem. I actually logged in as root and it still did not work. Unless you mean something else?

Regards, C

---

