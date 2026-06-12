---
title: "How much can I learn"
date: 2011-08-08
forum: General Help
---

### Post by tech291083 on 2011-08-08
Hi Friends,

I have two pcs both having Ubuntu 10.10. What can I learn with these two pcs only? 

Can I learning basic networking? 
File sharing? 
SSH? 
Client-server connection? 
Set up a MySQL database server?
Set up an application server? 
DHCP server? 
Print server? 
FTP server? 
File server?
Mail server?
can one pc be a firewall?

I have some topics in mind as I do happen to have a couple of Linux books with me, but do not really know as to how best these 2 pcs can be utilised for learning purpose. Please guide me as to what exactly I can learn. So that I can make the most of it. Weird query may be, but I am sure there are people with excellent suggestions to get me started in the right direction. Thanks.

---

### Post by haqking on 2011-08-08
> **tech291083 said:**
> Hi Friends,

I have two pcs both having Ubuntu 10.10. What can I learn with these two pcs only? 

Can I learning basic networking? 
File sharing? 
SSH? 
Client-server connection? 
Set up a MySQL database server?
Set up an application server? 
DHCP server? 
Print server? 
FTP server? 
File server?
Mail server?
can one pc be a firewall?

I have some topics in mind as I do happen to have a couple of Linux books with me, but do not really know as to how best these 2 pcs can be utilised for learning purpose. Please guide me as to what exactly I can learn. So that I can make the most of it. Weird query may be, but I am sure there are people with excellent suggestions to get me started in the right direction. Thanks.

Yes you can learn all of them, depending on the resources you use for reference and your capacity for knowledge.

Most of them are server services so you might to look at installing ubuntu server on one of the PC's or using virtualistion to do so.

this should proved answers to most of your questions.

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by sanderd17 on 2011-08-08
Exept for the basic networking, you can do everything with one PC if you use virtual machines. So if you don't have enough with 2 PCs, create virtual machines on one of them.

Some of them are even possible with one PC. You can have a MySQL server and client on the same computer. The same for the application server.

When you want to learn it, you just need to know the right tools (search for them on the internet and install them via synaptic or the software center). I do advise command-line tools because they make you learn better. Therefore, you first need to know a few basics of the command line, here is a little tutorial (it should only cost 5 minutes): [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by tech291083 on 2011-08-08
> **haqking said:**
> Yes you can learn all of them, depending on the resources you use...

Thanks God, it makes me so happy to learn that. I was actually reading one of the Linux bibles and has a section, section 4 may be, dedicated to networking etc, so I just asked all the things mentioned there in the book here in this thread of mine to you wonderful people. 

Resources wise - I have these two pcs, a switch and a small CAT5 cable. Slow net connection and a lot of enthusiasm. Can I make it?

>  Most of them are server services so you might to look at installing ubuntu server on one of the PC's or using virtualistion to do so.
[]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

Server services means software/packages meant for a specific task right? Like Apache for web, right? 

But is it really necessary for me to install Ubuntu server version on atleast one pc? I only have Ubuntu 10.10 desktop CD with me. Can't I do with it only? Sorry, no idea, so asking. If yes, then Ubuntu 10.10 server edition will be OK?

How do I do virtualisation? 
Thanks

---

### Post by tech291083 on 2011-08-08
> **sanderd17 said:**
> Exept for the basic networking, you can do everything with one PC if you use virtual machines. So if you don't have enough with 2 PCs, create virtual machines on one of them.


Ok, this is really encouraging news for me. Virtual machines. I need to know more about it. Is it a software package that I need to install? Thanks

Found something...

> A virtual machine (VM) is a software implementation of a machine (i.e. a computer) that executes programs like a physical machine.

[http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

There is a long list of various virtual machine software on this page, which one is the best fir for my Ubuntu 10.10 pc? Should be totally free and reliable, thanks

---

### Post by sanderd17 on 2011-08-08
> **tech291083 said:**
> 

Server services means software/packages meant for a specific task right? Like Apache for web, right? 

It mostly means that the "serving" part of the application is separated from the "viewing" part. You don't view web pages with Apache, but Apache serves them to your borwser.
> 

But is it really necessary for me to install Ubuntu server version on atleast one pc? I only have Ubuntu 10.10 desktop CD with me. Can't I do with it only? Sorry, no idea, so asking. If yes, then Ubuntu 10.10 server edition will be OK?

No, it's not necessary, the server version is just optimised for services (no desktop environment, other default packages and configurations ...). But you can do everything with the Desktop edition.
> 

How do I do virtualisation? 
Thanks

Take a look at VirtualBox (in the repositories) or VMware (closed source, but free for personal use).

You just open the app, create a virtual disk and choose to boot up from a CD or iso. That way you can install a virtual OS to the virtual disk.

---

### Post by haqking on 2011-08-08
> **sanderd17 said:**
> It mostly means that the "serving" part of the application is separated from the "viewing" part. You don't view web pages with Apache, but Apache serves them to your borwser.

No, it's not necessary, the server version is just optimised for services (no desktop environment, other default packages and configurations ...). But you can do everything with the Desktop edition.


Take a look at VirtualBox (in the repositories) or VMware (closed source, but free for personal use).

You just open the app, create a virtual disk and choose to boot up from a CD or iso. That way you can install a virtual OS to the virtual disk.

+1

However i would say go to [www.virtualbox.org](www.virtualbox.org) for latest version of virtualbox and download the .deb.

also download the extensions pack

---

### Post by tech291083 on 2011-08-08
> **sanderd17 said:**
> 
No, it's not necessary, the server version is just optimised for services .But you can do everything with the Desktop edition.

Good then. Really good.

>  Take a look at VirtualBox (in the repositories)...

You just open the app, create a virtual disk and choose to boot up from a CD or iso. That way you can install a virtual OS to the virtual disk.

Need to learn how to install this VirtualBox software on the net and on YouTube. I am gonna need some solid command to install this one, I think. See if I can find something Ubuntu 10.10 specific. Please feel free to guide me on this one. thanks

---

### Post by haqking on 2011-08-09
> **tech291083 said:**
> Good then. Really good.



Need to learn how to install this VirtualBox software on the net and on YouTube. I am gonna need some solid command to install this one, I think. See if I can find something Ubuntu 10.10 specific. Please feel free to guide me on this one. thanks


go to virtualbox using the link i provided earlier [www.virtualbox.org]("http://www.virtualbox.org")

download the version appropriate for you [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

then when the .deb file has downloaded double click it (it will install) done !

---

### Post by tech291083 on 2011-08-09
> **haqking said:**
> Most of them are server services so you might to look at installing ubuntu server on one of the PC's or using virtualistion to do so.

this should proved answers to most of your questions.

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Thanks the link is really useful. But I am a bit disappointed in the fact the what do I need to do learn basic networking using these 2 pcs.

---

### Post by haqking on 2011-08-09
> **tech291083 said:**
> Thanks the link is really useful. But I am a bit disappointed in the fact the what do I need to do learn basic networking using these 2 pcs.


[http://www.ezlan.net/basic.html](http://www.ezlan.net/basic.html)

[http://compnetworking.about.com/od/homenetworking/a/connecttwocomp.htm](http://compnetworking.about.com/od/homenetworking/a/connecttwocomp.htm)

you can use a crossover cable or a small hub/switch.

You have a switch and some cat 5 cables.  Plug the switch in, connect the cables to the PC's and switch and then it comes down to IP addressing etc on the PC's

this information cna be found from links provided.

enjoy

---

### Post by tech291083 on 2011-08-09
> **haqking said:**
> []("http://www.ezlan.net/basic.html")
you can use a crossover cable or a small hub/switch.

You have a switch and some cat 5 cables.  Plug the switch in, connect the cables to the PC's and switch and then it comes down to IP addressing etc on the PC's


Yes I do have a switch and some CAT 5 cables, but I had no idea whatsoever as to what I could do with them and how much I can learn in terms of networking, but now I am determined to learn and wish me luck, will get back to you with more headache (queries) for you as you are my best learning resource. thanks a lot, appreciated...............

---

