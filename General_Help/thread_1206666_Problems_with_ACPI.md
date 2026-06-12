---
title: "Problems with ACPI"
date: 2009-07-07
forum: General Help
---

### Post by superstoffer on 2009-07-07
Hello everybody,

I'm having problems with ACPI!

Each time I'm trying to install anything I get the following error:

* Starting ACPI services... acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.

I discovered the problem while trying to install VirtualBox 3.0 on Ubuntu 8.04 Hardy
In the following topic I got a lot of help, but couldn't solve the problem:

[http://ubuntuforums.org/showthread.php?p=7576114#post7576114](http://ubuntuforums.org/showthread.php?p=7576114#post7576114)

---

### Post by superstoffer on 2009-07-09
I have found out that the root of all my problems is due to the custom distro from OVH, which is on my box... I managed to change the distro-list to official Ubuntu and it solved my problems... 

I am new to Ubuntu/Linux, so I didn't notice that from the beginning...

---

