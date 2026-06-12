---
title: "VirtualBox networking"
date: 2010-11-11
forum: General Help
---

### Post by Ducatiboy Stu on 2010-11-11
I have a VM machine set up, which is a linux based PABX.

What I need to be able to do is setup the network between the VM and my host so that I can telnet and FTP into the VM to add backup files.

I can set the VM Linux IP address to whatever I need to...butg cant seem to talk between the two.

I dont need the VM to be able to access the interweb.


Host is Ubuntu 10.10

---

### Post by lmarmisa on 2010-11-11
The problem is probably due to use a NAT configuration in the network settings of your VM.

Try to switch to Bridged Adapter mode.

---

### Post by Ducatiboy Stu on 2010-11-11
Should I set the VM machine in the same subnet as the host

---

### Post by lmarmisa on 2010-11-11
Do you have a DHCP server in your LAN?.

In that case, the configuration is made automatically.

In the case of manual config, the answer is yes, you have to set the VM in the same subnet as the host (Bridged Adapter mode).

---

### Post by Ducatiboy Stu on 2010-11-11
The VM does not utilise DHCP, it has to be staticaly set

---

### Post by lmarmisa on 2010-11-11
> **Ducatiboy Stu said:**
> The VM does not utilise DHCP, it has to be staticaly set

Ok. Define the IP address for your VM in the same subnet as your host. If your router provides a DHCP service, do not use an IP address of its DCHP address pool.

This is an example:

Router IP address: 192.168.1.1
Subnet Mask: 255.255.255.0

DHCP Server - IP Address Range 192.168.1.50 - 192.168.1.149

In this case, you could assign the address 192.168.1.2 to your VM.

---

### Post by CharlesA on 2010-11-11
Use bridged networking instead of nat and you'll be good to go.

---

### Post by Ducatiboy Stu on 2010-11-11
That worked

Set VM to bridged mode and changed its IP to the same subnet as the host

:guitar:

---

### Post by lmarmisa on 2010-11-11
Great!!. :P

Please, mark the thread as SOLVED.

---

