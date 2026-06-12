---
title: "URGENT: dkpg error"
date: 2009-09-19
forum: General Help
---

### Post by Gianl09 on 2009-09-19
I was installing a package (Firefox 3.05 to be precise) using Synaptic when the process crashed. Now when I run *apt-get upddate *I get the error

*E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. *

I do what it says and run *sudo dpkg --configure -a.* I get the message

*dpkg: failed to link `/var/lib/dpkg/status' to `/var/lib/dpkg/status-old' for backup of status info: File exists*

I try to delete /var/lib/dpkg/status-old but I get

*rm: cannot remove `/var/lib/dpkg/status-old': No such file or directory*

The file, however, is there

[I]ubuntu@ubuntu:~$ ls /var/lib/dpkg
alternatives   cmethopt        info   statoverride      status-new  updates
available      diversions      lock   statoverride-old  status-old
available-old  diversions-old  parts  status            triggers[/I]

I am stuck. I have googled the first error but nobody seems to get the sequence I get. Any ideas of how can I fix my package management?

---

### Post by DougieFresh4U on 2009-09-19
Maybe try
**sudo apt-get -f install**

---

### Post by Gianl09 on 2009-09-19
Still get 

*E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. *

---

### Post by cesium62 on 2009-09-19
I think 'rm' might be giving you a misleading error message.  I would 'ls -l' the old file to see if there was anything funny with it.  I might 'ls -ld' the directories leading up to it.  Make sure you are super-user when trying to delete the file.

---

### Post by Gianl09 on 2009-09-19
As you can see I am using sudo

[I]gianluigi@ubuntu:~$ sudo rm /var/lib/dpkg/status-old
rm: cannot remove `/var/lib/dpkg/status-old': No such file or directory
gianluigi@ubuntu:~$ sudo ls /var/lib/dpkg
alternatives   cmethopt        info   statoverride    status-new  updates
available      diversions      lock   statoverride-old    status-old
available-old  diversions-old  parts  status        triggers[/I]

---

