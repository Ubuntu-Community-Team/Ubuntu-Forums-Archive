---
title: "VMware Virtual Machines Constantly Crash"
date: 2006-06-14
forum: General Help
---

### Post by Jæd on 2006-06-14
Hi, 

I'm trying to install Vmware Server Build 1.0.0-24927. I can install the server and start, but when I come to try and install an os in an VMware virtual machine (or do anything else with a virtual machine) I get an "internal monitor error - vcpu-0 DoubleFault". 

I've searched around I can't see this mentioned anywhere... I must be doing something obviously wrong... This Dapper, btw...

Thanks in advance...

J

---

### Post by The Darkness on 2006-06-14
You could try changing from vmxlsilogic to vmxbuslogic or vise versa depending on how you have it set now.

Not sure about ESX, but on VMware Workstaion, I have installed vmware-any-any-update101.tar.gz  (gotten from [http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/))
This has also fixed past issues with Workstation.

---

### Post by Jæd on 2006-06-15
VMware Server Beta is not the same as VMWare ESX Server...

---

