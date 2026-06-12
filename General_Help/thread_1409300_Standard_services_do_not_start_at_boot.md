---
title: "Standard services do not start at boot"
date: 2010-02-17
forum: General Help
---

### Post by sjorsvb on 2010-02-17
Hi all,

I've been running Ubuntu 9.10 since November '09, and since a month or so I'm having boot problems. Gnome starts, but some core services such as ssh and dnsmasq (that have started on boot somewhere in time), don't start anymore. Neither does rc.local fire, so I basically have to startup these things by hand. 

Also, I cannot get into the console anymore by using ctrl+alt+f*, because it gives a message like:
Starting ntpd
or
starting libgcrypt 1.4.4, or something in that fashion.

My belief is that something is holding the boot procedure in a waiting state before services such as ssh get to start, but I can't seem to find anything in the log files.

Can anybody help me?

Cheers,

Sjors

---

### Post by dummy910 on 2010-02-17
install the boot-up-manager for gnome titled 'bum'. it will show in your Administration Menu upon completion of the install.
```
sudo apt-get-bum
```

tinker with your settings from the gui interface from there.

---

### Post by sjorsvb on 2010-02-17
> **dummy910 said:**
> install the boot-up-manager for gnome titled 'bum'. it will show in your Administration Menu upon completion of the install.
```
sudo apt-get-bum
```

tinker with your settings from the gui interface from there.

I presume you mean ```
sudo apt-get install bum
```
however, I'm looking for a way to fix the problem, and not for a workaround, thanks

---

### Post by sjorsvb on 2010-02-17
I've found the solution: [https://bugs.launchpad.net/ureadahead/+bug/515788](https://bugs.launchpad.net/ureadahead/+bug/515788)
Thanks to another topic on this forum

---

