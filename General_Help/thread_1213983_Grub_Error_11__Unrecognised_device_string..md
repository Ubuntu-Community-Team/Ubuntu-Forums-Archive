---
title: "Grub Error 11 : Unrecognised device string."
date: 2009-07-15
forum: General Help
---

### Post by frmneo999 on 2009-07-15
Seeking help from all Linux pros here

When I tried to restart my system after an update, its showing

> Error 11 : Unrecognised device string.

I tried to boot to the recovery option and also to the older kernel version shown in the boot list. But it all ended up with the same error. I also tried my luck with the live cd. I mounted the harddisk and changed the root folder the harddisk by :

> ubuntu@ubuntu:~$ sudo chroot /media/disk su

and tried 
> apt-get update
The error was :
> 
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Get: 1 Link jaunty Release.gpg [189B]
Ign Link jaunty/partner Translation-en_GB
Get: 2 Link jaunty Release.gpg [189B]
Hit Link jaunty/main Translation-en_GB
Hit Link jaunty/restricted Translation-en_GB
Hit Link jaunty/universe Translation-en_GB
Hit Link jaunty/multiverse Translation-en_GB
Get: 3 Link jaunty-updates Release.gpg [189B]
Ign Link jaunty-updates/main Translation-en_GB
98% [Working]FATAL -> Could not set non-blocking flag Bad file descriptor
E: Method http has died unexpectedly!

Is there any possible way I can rescue the system as I spent a reasonable time to set it up for my development.

Possible causes of the issue :

* I blindly entered the debian source in the source list first while following a documentation for installing my development environment. An update command was also executed, but it was soon changed back to ubuntu urls. ( The boot menu now shows as Debian ........ instead of Ubuntu.. ). So it may be a reason. But the same mistake was done in another system here and the system is working perfectly.

* A system update was done today and the problem was right after restarting the system. Even thought the window showed "Update completed. Please restart the system" I couldn't restart it through terminal or GUI . It continuously showed an error "command timed out' . So had to hard reboot the system .

Any idea how to rescue my system?? Thanks in advance!

---

### Post by master_kernel on 2009-07-15
Boot into the live cd and run:
```
sudo fsck /dev/YOURHDDHERE
```

This will check your filesystem to make sure it's OK.

---

