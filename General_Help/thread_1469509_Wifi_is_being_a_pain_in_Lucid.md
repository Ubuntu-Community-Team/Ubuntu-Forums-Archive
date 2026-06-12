---
title: "Wifi is being a pain in Lucid"
date: 2010-05-02
forum: General Help
---

### Post by Monotoko on 2010-05-02
Hiya :)

I'm having some issues getting wifi working on a Dell Inspiron Mini 1011 running lucid, originally it said "Device Not Ready" under the network manager, after installing the proprietary drivers, it now shows the networks...but whenever i try and connect to any network, it fails and comes back asking for the key, even though i know its right.

If i take the key off the router then try to connect, it just tries for about 3 minutes, then fails.

---

### Post by Monotoko on 2010-05-02
bump

---

### Post by zaphod777 on 2010-05-02
You might try installing the backports package but I don't see it in the repos yet. 

try and install the latest bleeding edge wireless drivers just extract the file and read the readme file it is pretty easy. This fixed all wireless issues I had before.

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) :
> You can get bleeding edge compat-wireless here:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

This package is updated daily. It reflects the latest on linux-next.git tree.

---

### Post by Monotoko on 2010-05-02
thats just taken me a step backwards, now it doesnt even recognise the fact that there is a wireless driver in there, the only connection i have under the connection manager is wired -.-

---

### Post by zaphod777 on 2010-05-02
did you reboot after?

---

### Post by Monotoko on 2010-05-02
3 times, i also uninstalled the proprietary driver and reinstalled it.

---

### Post by zaphod777 on 2010-05-02
what wireless card are you using? I will see if I can google around and find something.

---

### Post by Monotoko on 2010-05-02
Network Controller: Broadcom Corporation BCM4312

I have had a google around but it tells me to install the STA drivers (the one provided in the hardware drivers manager) but again...it doesn't work, only gives me the network list, doesnt actually connect

---

### Post by zaphod777 on 2010-05-02
hmm there seams to  be a lot of users having problems with that card in 10.04 

I found this bug you might want to post your results there.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563308](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563308)

Acording to 
[http://ubuntuforums.org/showthread.php?t=1441435](http://ubuntuforums.org/showthread.php?t=1441435)
try
```
sudo apt-get install bcmwl-kernel-source
```

or actually looks like these guys maybe have a solution.

[http://ubuntuforums.org/showthread.php?t=1266620&page=66](http://ubuntuforums.org/showthread.php?t=1266620&page=66)

---

