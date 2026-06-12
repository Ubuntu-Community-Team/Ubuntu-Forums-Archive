---
title: "how to install vmware workstation 5 on ubuntu ?"
date: 2006-01-27
forum: General Help
---

### Post by niccolo.canestrari on 2006-01-27
does anybody knows?

---

### Post by MartinG on 2006-01-27
Yes. Lots of us have done it, the instructions are pretty clear (reference below). What's the problem?

[http://www.vmware.com/support/ws55/doc/index.html](http://www.vmware.com/support/ws55/doc/index.html)

PS
Trying to guess, if there is a problem the usual one is that the installer tries to build a new kernel module and fails.  The full solution, assuming you have not done some of this already, is as follows:```
sudo apt-get install build-essential gcc-3.4 linux-headers-`uname -r`
export CC=gcc-3.4
sudo <vmware_install_command>
```

---

