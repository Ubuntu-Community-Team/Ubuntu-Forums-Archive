---
title: "problem in ubuntu."
date: 2012-05-02
forum: General Help
---

### Post by ramanathan on 2012-05-02
ramanathan@ramanathan:~$ sudo su
[sudo] password for ramanathan: 
root@ramanathan:/home/ramanathan# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
root@ramanathan:/home/ramanathan# 


i try to upgrade the version ubuntu 12.04 unfortunately i closed my laptop after when i try to upgrade the error occurs................

---

### Post by billyseth on 2012-05-02
an apt process is still running somewhere, you could try ps -A to get a list of running processes, then kill the related one, but also a simple system restart should do the trick

---

### Post by ramanathan on 2012-05-02
> **billyseth said:**
> an apt process is still running somewhere, you could try ps -A to get a list of running processes, then kill the related one, but also a simple system restart should do the trick

how to kill the process............

---

### Post by billyseth on 2012-05-02
sorry, use 

killall -9 processName

---

### Post by radix018 on 2012-05-19
U need to delete the lock file

sudo rm /var/lib/apt/lists/lock

and also from the cache

sudo rm /var/cache/apt/archives/lock

and run the apt-get again !

---

