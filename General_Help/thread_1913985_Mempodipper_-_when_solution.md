---
title: "Mempodipper - when solution?"
date: 2012-01-23
forum: General Help
---

### Post by sanderj on 2012-01-23
Hi,

Does anybody know when Ubuntu/Canonical will provide a bugfix for the Mempodipper local root vulnerability? Is that a matter of hours, or days, or longer?

I checked my system (Ubuntu 11.10, Linux 3.0.0-12), and it is vulnerable ... :( (EDIT: This is my VPS: it has Ubuntu 3.0.0-12.20-server 3.0.4)


I see nothing on [https://bugs.launchpad.net/ubuntu/?field.searchtext=mempodipper&search=Search](https://bugs.launchpad.net/ubuntu/?field.searchtext=mempodipper&search=Search) ...

---

### Post by sanderj on 2012-01-23
Ah, that's fast:

My laptop is running Ubuntu 11.10 with 3.0.0-15-generic. The dmesg shows "Ubuntu 3.0.0-15.25-generic". I checked and the system is vulnerable.

However, after a "sudo apt-get update", "sudo apt-get upgrade" and system reboot, I now have Ubuntu 3.0.0-15.26-generic (according to dmesg), and ... it's not vulnerable anymore.


My VPS is still on -12, so I guess they are lagging behind ... :(

---

### Post by stefangr1 on 2012-01-23
> **sanderj said:**
> 
However, after a "sudo apt-get update", "sudo apt-get upgrade" and system reboot, I now have Ubuntu 3.0.0-15.26-generic (according to dmesg), and ... it's not vulnerable anymore.

On my system the [shell code]("http://blog.zx2c4.com/749") can still being injected after apt-get update, upgrade and rebooting.

Though it was fun to try out a security hack that actually works on my system, I must say I find this very problematic. For example, with my ISP every user has access to a linux shell server. I'm afraid the shell code is going to work there as well, which basically means that everyone can get access to the entire system.

I hope an update is going to be available soon.

---

### Post by sanderj on 2012-01-23
My VPS went from 3.0.0-12-server tot 3.0.0-15-server (Ubuntu 3.0.0-15.26-server 3.0.13), and the vulnerability is ... gone. :D

---

