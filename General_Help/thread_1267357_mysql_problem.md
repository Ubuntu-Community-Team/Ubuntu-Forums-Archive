---
title: "mysql problem"
date: 2009-09-15
forum: General Help
---

### Post by fchieli on 2009-09-15
Using Ubuntu Server 9.04
Right after installation everything was working fine
Aster running all the updates and rebooting I can't access mysql server from phpmyadmin, I get a #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured).... error.
On the machine itself I can sudo mysqld and after that everything goes back to normal, until I reboot again.
I'm a beginner, here's more info:

In the startup sequence OpenBSD sshd loads succesfully
mysqld fails
then OpenBSD sshd restarts

Right after rebooting, if I run ps aux | grep mysqld
I get nothing
so mysqld is not running
I have to sudo mysqld and everything goes back to normal
I can I find out what prevents mysqld to start ?
Thanks!
federico

---

### Post by DaithiF on 2009-09-15
Hi, 
I'm curious if you see an error on startup indicating that mysqld has failed to start, or are you inferring that it failed to start because it is not running when you look for it with ps.

If the first of those, is there an error reported, and can you post it here if so.

If not, then first thing I would try is to reset the runlevel links to make sure that mysqld gets started at boot.
```
sudo update-rc.d mysql defaults
```

---

### Post by fchieli on 2009-09-15
I'm a dumbass...!
Realized there was no loopback in my network interface configuration...
sorry I'm an absolute beginner...
all good now!
federico

---

### Post by gurukatre on 2010-05-16
> **fchieli said:**
> Using Ubuntu Server 9.04
Right after installation everything was working fine
Aster running all the updates and rebooting I can't access mysql server  from phpmyadmin, I get a #2002 - The server is not responding (or the  local MySQL server's socket is not correctly configured).... error.
On the machine itself I can sudo mysqld and after that everything goes  back to normal, until I reboot again.
I'm a beginner, here's more info:

In the startup sequence OpenBSD sshd loads succesfully
mysqld fails
then OpenBSD sshd restarts

Right after rebooting, if I run ps aux | grep mysqld
I get nothing
so mysqld is not running
I have to sudo mysqld and everything goes back to normal
I can I find out what prevents mysqld to start ?
Thanks!
federico




hi look at the following post problem has been solved 

[http://ubuntuforums.org/showthread.php?t=1484736](http://ubuntuforums.org/showthread.php?t=1484736)                   :KS

---

