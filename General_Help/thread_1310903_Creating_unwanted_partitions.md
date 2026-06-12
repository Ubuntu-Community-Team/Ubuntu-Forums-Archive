---
title: "Creating unwanted partitions"
date: 2009-11-02
forum: General Help
---

### Post by truckbytes on 2009-11-02
I installed 9.04 about 2 weeks ago on a new Lenovo G550 laptop. Installation and partitioning beside Vista went perfect. However each time I use "Restart" in Ubuntu it creates a new mount for Ubuntu when it starts back up. I checked the partitions and there is not an actual new partitions, but that is what it looks like when it reboots. I.E. it lists 3 different Ubuntu's and there recovery mode options and then Vista.

Any ideas how to get rid of these annoying extra Ubuntu's to boot from and how to make it quit happening?

Thanks
Joel

---

### Post by ColdFFF on 2009-11-02
In this case there are no extra partitions.

What you are seeing is Ubuntu's default boot manager - GRUB - listing Ubuntu and its recovery mode for each version of the Linux kernel on your machine.

Your options to cut these entries down are:

1) Uninstall the older kernels (it is recommended to keep at least 1 extra kernel to roll back to if the current kernel stops working for you)

2) Edit the GRUB menu to remove the unwanted entries. The easiest way to edit this is to install startupmanager via synaptic, which provides a simple GUI to remove them. Alternatively you can manually edit /boot/grub/menu.lst , but I would advise reading up before attempting this.
A good reference is [Hermans Grub Guide]("http://members.iinet.net.au/~herman546/p15.html")

---

### Post by truckbytes on 2009-11-02
Thank You! :D

So if I understand you correctly, these are not a problem and in if i use the "restart" again I won't see any more added either? It also sounds like it could be a good idea to just leave them alone in case they are needed if they aren't causing any harm or taking up HD space.

Thank you
Joel

---

### Post by ColdFFF on 2009-11-02
Unless theres some other problem that is affecting grub, you should only see extra options when a new kernel is installed.

For the sake of your own sanity I would only keep 2 kernels listed on your boot menu though.

---

