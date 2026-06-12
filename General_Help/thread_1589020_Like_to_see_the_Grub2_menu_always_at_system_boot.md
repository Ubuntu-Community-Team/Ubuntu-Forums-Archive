---
title: "Like to see the Grub2 menu always at system boot"
date: 2010-10-05
forum: General Help
---

### Post by HiSiskin on 2010-10-05
As a long time Red Hat/Fedora user, I'm quite new to the Ubuntu/Debian culture, and/or,  to the Grub2 specific behavior.

I'd like to see Grub2 system selection menu at every boot time even if I only have a single operating system, Ubuntu 9.10, on my hard drive. What should I do fot this purpose?

Thanks in advance.

---

### Post by andrewthomas on 2010-10-05
edit /etc/default/grub 
 
with 
```
gksudo gedit /etc/default/grub
```
 
so GRUB_HIDDEN_TIMEOUT=0 is commented
 
```
GRUB_DEFAULT=0
 #GRUB_HIDDEN_TIMEOUT=0
 GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT=10
```
 
 
 
 
 
[http://ubuntuforums.org/showpost.php?p=9791499&postcount=2](http://ubuntuforums.org/showpost.php?p=9791499&postcount=2)

---

