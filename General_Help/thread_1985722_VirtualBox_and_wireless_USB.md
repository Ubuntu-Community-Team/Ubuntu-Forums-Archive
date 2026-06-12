---
title: "VirtualBox and wireless USB?"
date: 2012-05-23
forum: General Help
---

### Post by zozza on 2012-05-23
Hi, 

I use Ubuntu 10.04 and have installed the PUEL (Personal Use and Evaluation Licence) version of VirtualBox.

I have installed XP SP3 in the virtual machine. 

I am not sure it is possible to do what I want to achieve.

I want to get a mobile broadband USB, install it in XP (inside the VirtualBox), then be able to use it with both XP and Ubuntu.

Is this possible?  

Thanks

---

### Post by haqking on 2012-05-23
> **zozza said:**
> Hi, 

I use Ubuntu 10.04 and have installed the PUEL (Personal Use and Evaluation Licence) version of VirtualBox.

I have installed XP SP3 in the virtual machine. 

I am not sure it is possible to do what I want to achieve.

I want to get a mobile broadband USB, install it in XP (inside the VirtualBox), then be able to use it with both XP and Ubuntu.

Is this possible?  

Thanks

yes, but not at the same time. When you mount it in the VM it dismounts from the host OS. Unless you mean you want internet access from it in both at the same time, in which case set it up in your host and then NAT or bridge to it from the VM.

You also need to be in the vboxusers group and have the extension pack installed.

oh and make sure you are running the latest virtualbox for best performance, its currently 4.1.16 just grab the .deb from here [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html) if you dont have it already.

Peace

---

