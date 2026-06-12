---
title: "Cant add or delete users?"
date: 2011-04-05
forum: General Help
---

### Post by airplanesimen on 2011-04-05
I have tried to add AND delete users at my ubuntu 10.10, in the terminal and the management. 

In the terminal it appeared this text when i tried to add "adminis":

$ 
simen@Windows:~$ sudo adduser adminis
Adding user `adminis' ...
Adding new group `adminis' (1004) ...
Adding new user `adminis' (1002) with group `adminis' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /home/adminis -g adminis -s /bin/bash -u 1002 adminis' returned error code 1. Exiting.

I have all the administrative rights, because im an administrator.

at the user settings it is popping up a message that says:

The configuration could not be saved
You are not allowed to modify the system configuration.

Any suggestions how to fix this?:confused:

(warning: not proper english:P)

---

### Post by falko on 2011-04-05
Can you try to become root...
```
sudo su
```
... and then run
```
adduser adminis
```
?

---

### Post by airplanesimen on 2011-04-06
> **falko said:**
> Can you try to become root...
```
sudo su
```
... and then run
```
adduser adminis
```
?

i found a reason why i cant do this... I'm using ssh, and someone have tricked me. when i did that above, it stands that i am not in the sudoers file. but im going fix this, Thanks for your help:)

---

