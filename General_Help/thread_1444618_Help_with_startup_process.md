---
title: "Help with startup process"
date: 2010-04-01
forum: General Help
---

### Post by Nedben on 2010-04-01
Hi,

I am new to Ubuntu.
I've gone through the initialization scripts trying to find where or at which stage /etc/init.d/networking.conf is called. So far, I was not able to figure out which script starts the network services when the system boots.
My objective is to start the firewall before the system enables my ethernet connection.
Can someone help me? Thanks.

---

### Post by moetunes on 2010-04-01
In /etc/rc2.d are the symlinks to the file in /etc/init.d. They are given numbers which determine the order they are run. The files that start with k stop a service and the ones that start with s start a service. Be very careful changing anything to do with the boot process. Hope that gives you a clue. :)

---

### Post by Nedben on 2010-04-01
Thanks for responding.
I know how to start and stop services depending on the runlevels.
My problem is that I cannot find at which stage the networking services are turned on.
I've looked in places like /etc/rc.d/rcS/, /etc/rc.d/rc2.d/ (the default runlevel) and /etc/init/rcS (replaced /etc/inittab), but I can't find anything referring to Sxynetworking (with xy being numbers) or /etc/init.d/networking.conf.
I've even Googled it under Ubuntu and Debian before submitting this post.

---

