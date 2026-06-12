---
title: "Missing Packages?!"
date: 2006-06-18
forum: General Help
---

### Post by Mr. Picklesworth on 2006-06-18
I searched for linux-headers-2.6.15-25 at packages.ubuntu.com today, and it has finally appeared there since the big update. (Sorry if there has been another update since then and I'm confusing you; I wouldn't know because it broke my wireless and then I poked at it with a stick for a while which seems to have killed it in the 2.16.15-23 kernel as well).

So, I followed that link...
[http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-25](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-25)
> Not Found
The requested URL /dapper/devel/linux-headers-2.6.15-25 was not found on this server.

In fact, none of the 2.6.15-25 linux-headers packages are there. I (think that I) need this package to fix wireless.
Is this a common error and soon to be fixed, or is there a different link that I can try?

Thanks in advance!

---

### Post by Ramses de Norre on 2006-06-18
They're in my repos.. Do you have the restricted repos enabled?

> ramses@icarus:~$ apt-cache search linux-headers-2.6.15-25
linux-headers-2.6.15-25 - Header files related to Linux kernel version 2.6.15
linux-headers-2.6.15-25-386 - Linux kernel headers 2.6.15 on 386
linux-headers-2.6.15-25-686 - Linux kernel headers 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
linux-headers-2.6.15-25-k7 - Linux kernel headers 2.6.15 on AMD K7 SMP/UP
linux-headers-2.6.15-25-server - Linux kernel headers 2.6.15 on Server Equipment
linux-headers-2.6.15-25-server-bigiron - Linux kernel headers 2.6.15 on BigIron Server Equipment


---

### Post by Mr. Picklesworth on 2006-06-18
The problem is, I'm trying to get it through another (Windows) computer without hauling around that other ghastly machine which is currently disconnected from the network.

The smart thing to do, of course, is to move the ugly computer and plug it in with a network cable, but it just seems weird to me that the package is unavailable off the web site.

---

### Post by Mr. Picklesworth on 2006-06-19
Okay, I got it through Synaptic Package Manager with a LAN cable.

Sorry about the double post... I hit the wrong button :S
(Meant to edit, then I wandered away and forgot that I was in the wrong screen)


This did fix my wireless troubles, btw... so anyone having trouble with wireless on the new kernel, just recompile ndiswrapper with the new linux-headers.
Probably wouldn't be a bad idea for the developers to do something that automatically releases recompiled versions of software like ndiswrapper on the event of a kernel update... It would be a neat addition and would really speed Ubuntu ahead :)

---

