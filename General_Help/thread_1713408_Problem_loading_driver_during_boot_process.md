---
title: "Problem loading driver during boot process"
date: 2011-03-24
forum: General Help
---

### Post by euler85 on 2011-03-24
Hi, I'm a very new user and I hope very active since right now!
 
My problem is the following:
 
I've bought a CAN-PCI card (it's a common PCI Card which implements CANbus protocol, used in vehicles) and followed the instructions for its installation.
 
After all it was working perfectly but, every time I shut down or reboot my pc, the card is not detected and I have to reinstall the driver to use it properly.
 
I've contacted the supplier but he answered me:
 
[I][B][COLOR=black]The Linux distrubutions are using different ways to load the driver during boot process and link it to an inode. The installation guide from our README file is independent of the distribution. Unfortunately we could not pay attention to every distribution, due to the huge effort. To implement the start of the driver in your boot process you have to contact the community of your distribution. I am very sorry, that I could not help you in this case.
So I can't have any help from them.[/COLOR]
[/B][/I] 
The commands that I've to repeat every time I reboot my pc are:
[INDENT]From the working directory /dev:
 
[I][B]sudo mknod --mode=a+rw can0 c 54 0
sudo mknod --mode=a+rw can1 c 54 1[/B][/I]
[I]
[/I]From the directory where the compiled driver is:

***sudo insmod esdcan-pci200.ko***
[/INDENT]And it starts working perfectly…
 
The /var/log/messages show no problems after every installation:
 
*esdcan_pci200: module license 'Proprietary' taints kernel.*
*Disabling lock debugging due to kernel taint*
*esd CAN driver: Hardware-version = 1.0.00*
*esd CAN driver: Card = 0 Minor(s) = 0, 1,*
*esd CAN driver: CAN_PCI2xx*
*esd CAN driver: baudrate not set*
*esd CAN driver: mode = 0x00000000, major = 54, verbose = 0x00000001*
*esd CAN driver: version 3.8.20 13:26:48 Mar 18 2011: successfully loaded*
 
The driver is also placed in all these folders (because I don't know where else can I place it):
 
[I]/lib/modules/2.6.31-22-generic/esdcan-pci200.ko
/lib/modules/2.6.31-22-generic/kernel/drivers/pci/esdcan-pci200.ko
/lib/modules/2.6.31-22-generic/kernel/drivers/pci/hotplug/esdcan-pci200.ko
/lib/modules/2.6.31-9-rt/esdcan-pci200.ko
/lib/modules/2.6.31-9-rt/kernel/drivers/pci/esdcan-pci200.ko
/lib/modules/2.6.31-9-rt/kernel/drivers/pci/hotplug/esdcan-pci200.ko
/lib/modules/2.6.31-20-generic/esdcan-pci200.ko
/lib/modules/2.6.31-20-generic/kernel/drivers/pci/esdcan-pci200.ko
/lib/modules/2.6.31-20-generic/kernel/drivers/pci/hotplug/esdcan-pci200.ko
/lib/modules/2.6.31-14-generic/esdcan-pci200.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/pci/esdcan-pci200.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/pci/hotplug/esdcan-pci200.ko[/I]
 
But I don’t know what can I do more to solve this problem…
 
Could you help me?

Thanks.

---

### Post by euler85 on 2011-03-25
Nobody? :(

---

### Post by euler85 on 2011-04-01
Does anybody know any solution? Thank you :)

---

