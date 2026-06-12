---
title: "Dapper Server Boot Freeze"
date: 2006-06-03
forum: General Help
---

### Post by pinlu on 2006-06-03
before the official release of the dapper server edition. i used to install dapper rc6 in server mode. everything works. i just tried the new dapper server cd. installation went ok on my via m10000 board. however, when machine is rebooted, after the kernel is decompressed, the machine freezes. installation with the new desktop version works. i suspect it is caused by the server kernel (SMP).

any ideas?

---

### Post by GarlicFish on 2006-06-03
Just looking at the same problem using VMWare and Dapper Server.

If you reboot the install CD into rescue mode after the initial install has hung, you can mount the file systems and apt-get another kernel (386 or 686).  It boots fine after this.

---

