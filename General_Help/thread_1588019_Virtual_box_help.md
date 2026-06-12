---
title: "Virtual box help"
date: 2010-10-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-04
My laptop's ip is 192.168.1.44 and my Virtual Box's ip of 10.0.2.15
i need to be able to ping 10.0.2.15 from my desktop 192.168.1.101
any idea how i can make 10.0.2.15 visible on the network? or mask it as 192.168.1.44

---

### Post by lukeiamyourfather on 2010-10-04
If you know the ports you need then you can forward those specific ports to the virtual machine since the default network is a NAT configuration. So the rest of the network would see the virtual machine from the host IP address, except for certain ports would be answered by the virtual machine instead of the host operating system.

If you want the virtual machine to have an IP address for itself and look like a physical computer on the network then you'll need to use bridged networking. This means the virtual machine will use a physical network adapter on the host and get an IP address from the DHCP server on the network just like every other computer.

---

### Post by Rychoo on 2010-10-04
Go to the settings and at Network tab select Bridged Adapter
then you can set virtual machine ip to some witch fit to your network in that case 192.168.1.*

---

### Post by pqwoerituytrueiwoq on 2010-10-04
> **Rychoo said:**
> Go to the settings and at Network tab select Bridged Adapter
then you can set virtual machine ip to some witch fit to your network in that case 192.168.1.*
yay for simple answer :)

---

