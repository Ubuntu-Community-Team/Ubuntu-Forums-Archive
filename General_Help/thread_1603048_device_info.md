---
title: "device info"
date: 2010-10-22
forum: General Help
---

### Post by ub007 on 2010-10-22
Hi

> /devices/pci0000:00/0000:00:01.0/0000:01:0d.0/0000:02:02.1/irq

Is there anyway to know which device the above is this referring to?

> [root@myserver 0000:02:02.1]# ls
broken_parity_status  device  local_cpus  resource          subsystem_vendor
bus                   driver  modalias    resource0         uevent
class                 enable  net:eth1    subsystem         vendor
config                irq     power       subsystem_device
[root@mtserver 0000:02:02.1]# cat vendor
0x14e4
[root@myserver 0000:02:02.1]# cat device
0x1648

Thanks in advance
David

---

### Post by Hippytaff on 2010-10-22
> 
class enable net:eth1 subsystem vendor

Is it ethernet controller?

---

### Post by ub007 on 2010-10-22
Yep, it was NIC card :)

---

