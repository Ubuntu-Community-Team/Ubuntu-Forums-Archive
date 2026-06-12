---
title: "Installing VMware Player help"
date: 2006-03-29
forum: General Help
---

### Post by blackjack6.21.91 on 2006-03-29
Having trouble installing VMware player on i386 machine.
Installed the default linux .tar package.
Failure comes up during terminal install.  The session is below
I specified the default folder locations for everything until the error came up, and tried it as root use, same situation

ben@ben:~$ sudo perl /home/ben/Desktop/vmware-player-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

[I]Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.[/I]

---

