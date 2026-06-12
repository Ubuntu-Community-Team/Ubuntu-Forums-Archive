---
title: "Uninstalling VirtualBox..."
date: 2009-06-26
forum: General Help
---

### Post by notfound123 on 2009-06-26
I uninstalled virtualbox-2.2 from Jaunty (2.6.28-11). Everything looks nice and clean with one exception:

when the system starts, i get 

"Starting VirtualBox kernel module..... [fail]"

Strange, because my VirtualBox is gone for sure. I found one discussion suggesting to recompile the kernel image... Is it necessary? How do I do that?

---

### Post by RedSingularity on 2009-06-26
Try in terminal,

sudo apt-get purge virtualbox*

---

### Post by synapsys on 2009-06-26
There is a big difference between a kernel image and a kernel module. Something is still trying to load the virtualbox kernel module, but it has been removed so you are getting a fail. As mentioned above, you need to completely remove all traces, so there is no reason to try and call the kernel module.

---

### Post by notfound123 on 2009-06-26
I had tried apt-get purge earlier... didn't fix it.  Any other suggestions? Thanks.

---

### Post by synapsys on 2009-06-27
Try blacklisting vboxdrv....

---

### Post by siryuhan on 2009-06-27
Try editing /etc/rc.conf and removing vboxdrv under modules. Or actually, grep vboxdrv * in /etc and remove all references to it.

---

### Post by notfound123 on 2009-06-27
It worked. Thanks.

---

