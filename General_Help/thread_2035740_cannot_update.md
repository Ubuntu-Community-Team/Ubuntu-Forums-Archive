---
title: "cannot update"
date: 2012-07-31
forum: General Help
---

### Post by tobythedog on 2012-07-31
just tried to update , says the package system is broken and to run  apt-get install -f
when i do this i get the following problem,E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tony@ubuntu-laptop-1:~$ 

i am signed in as root , anyone any idea how to fix this please

---

### Post by albandy on 2012-07-31
you should type sudo before apt 

sudo apt-get install -f


I think you are not running under root, type whoami in the terminal.

---

### Post by drs305 on 2012-07-31
As *albandy* stated, you must run the command as root. Additionally, if you are still getting the 'lock' error message, make sure all other installation apps such as Synaptic, Update Manager, and Ubuntu Software Center are closed.

When these GUI applications are running they will prevent you from accomplishing the same tasks from the command line. Closing the apps should 'unlock' APT and allow the terminal commands to work.

In some instances, the lock remains in place. In this case try rebooting the system, which usually will clear the lock and allow you to run the commands from the command line.

---

### Post by tobythedog on 2012-07-31
thanks for the help , the sudo did the trick

---

