---
title: "Can't install VMware"
date: 2005-02-24
forum: General Help
---

### Post by Rock on 2005-02-24
Everytime I try to install VMware, I get this error.
root@linuxboard:/home/chris # /home/chris/vmware-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

root@linuxboard:/home/chris #

---

### Post by Quest-Master on 2005-02-24
Do it with "sudo."

# sudo /home/chris/vmware-distrib/vmware-install.pl

---

### Post by Jansons on 2005-03-09
I'm getting this error on install, too..

sudo is not helping. I tried to copy this file from cmd line with same access rights and it worked.

What should I do?

---

