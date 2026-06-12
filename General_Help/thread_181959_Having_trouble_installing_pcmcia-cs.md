---
title: "Having trouble installing pcmcia-cs"
date: 2006-05-25
forum: General Help
---

### Post by GelflingOne on 2006-05-25
First of all, i'm a newbie.
Sorry if i'm not complete enough with givving information you might need.

I have bought a pcmcia card (Linksys WPC11 ver3) which should work properly with Hermes chipset 802.11b (Orinoco/Prism2/Symbol).
I followed the instructions as far I could from [http://justlinux.com/forum/archive/index.php/t-112138.html]("http://justlinux.com/forum/archive/index.php/t-112138.html").

I am running ubuntu 2.6.12-10-386
I have placed latest stable kernel (from kernel.org) in /lib/modules/linux-2.6.12.6 .
I am trying to install pcmcia-cs-3.2.8 

When I "make config" i get the following error:

Hmmm... /sbin/ksyms is broken. Using /proc/ksyms...
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
cat: /proc/ksyms: No such file or directory
and so on...

what is ksyms? I cannot find much about it on the net. It should be a command, but i cannot find it. I can't install it with apt-get or synaptic package manager.

How can I solve this problem?

I'm really getting frustrated right now. 

Gelfling.

---

### Post by GelflingOne on 2006-05-26
Well? no-one?
There must be a guru who can point me in the right direction.

---

### Post by Sutekh on 2006-05-26
I'm no guru.  

Are you having problems with the pcmcia card services that come with Ubuntu by default?  They should already be installed, but if not can be done with this command.
```
sudo apt-get install pcmcia-cs
``` 
In Breezy the version is 3.2.5.  In Dapper the version is 3.2.8.

So you could consider getting Ubuntu Dapper if the Breezy version (3.2.5) doesn't work. 


If this is not the option you want to take, and you want to install the latest pcmcia-cs source code (3.2.8) and compile it in Breezy, then you should do this against the 2.6.12-10-386 kernel.   This means you need the 2.6.12-10-386 kernel headers, not the latest kernel sources.

This is where I'd get the pcmcia-cs source code (you may have gone here too)

[SourceForge.net - pcmcia-cs]("http://sourceforge.net/project/showfiles.php?group_id=2405&package_id=2373")

This is how I'd install the kernel headers for the Breezy kernel
```
sudo apt-get install linux-headers-2.6.12-10-386
``` Then try installing the pcmcia-cs source code again.

---

### Post by GelflingOne on 2006-05-29
Thank you for your reply.
I had already downloaded the kernel headers. 
That did not work, so I downloaded the complete kernel source from kernel.org.
I think I messed up a thing or two.
I'm going to install ubuntu from scratch again and write down all steps I preformed. Maybe that will clear some things out.

---

