---
title: "static ip bridged with Virtualbox"
date: 2011-10-15
forum: General Help
---

### Post by theluli on 2011-10-15
Hi

Here is the thing

l am using mint debian edition , l have conf a static ip , and l have install virtualbox,
so the thing is that l am trying to do is ....how can conf my pc to ssh or to telnet to the virtual host machine , l'v been trying since two days to found anything what is helpful but nothing

---

### Post by Perfect Storm on 2011-10-16
Moved to Other OS/Distro Talk.

---

### Post by haqking on 2011-10-16
> **theluli said:**
> Hi

Here is the thing

l am using mint debian edition , l have conf a static ip , and l have install virtualbox,
so the thing is that l am trying to do is ....how can conf my pc to ssh or to telnet to the virtual host machine , l'v been trying since two days to found anything what is helpful but nothing

What OS is in the Virtual machine ?

Does it have SSH installed ?

is the VM static IP the same subnet as the host with same gateway ?

is the VM network adapter bound to the correct host adapter ?

can you ping the VM or can the VM ping the host.

We need more information

---

### Post by theluli on 2011-10-24
Hi

l changed my host machine to Ubuntu 10.10, and l tried again , on VM l have installed fedora, windows server2008 and debian , l can ping , but l can not SSH from host machine to VM , but from VM to host machine l can 

Maybe l am doing something wrong on VM network interfaces ?

Can you advise me how can l setup network in VM

---

### Post by Perfect Storm on 2011-10-24
Thread moved back.

---

### Post by theluli on 2011-10-24
Hi

Sims that now is working , l manage to setup somehow bridge on ubuntu host , and when l check with command ifconfig l got bro and also virbr0 , so than l start VM and in network l select bridge adapter and the name virbr0 and than l got a different network ip , is this normal ? or l should sign an ip as a static from my range of network ???

And to mention , that when l start to machine in VM , one is geting eth0 and the other one is geting eth1 ?!

Is this good ??

---

### Post by drdos2006 on 2011-10-24
Hi there,

Set up your VM settings or VirtualBox settings with the VM NIC ( Network Interface Card ) in bridged mode to receive an IP address which is on your LAN subnet IP addresses.

Once your VM is up and running, select a fixed IP address within your VM, using the same subnet as your LAN.

You can find out which NIC to use from the terminal and "ifconfig".
Configure that NIC for the fixed IP address.

regards

---

### Post by theluli on 2011-10-25
Hi drdos2006

Thanks for your help , but when l select bridge adapter on VM also under name l have:
br0
eth0
eth1
tap0
vmnet1 -vmware player
vmnet2 -vmware player
vribr0

So when l check the ip and interface on VM machine , a got there eth0 and Lo
So das the eth0 represent dhe host machine or guest machine ????

Yesterday l tried with vribr0 , and it worked , but l am not sure whether is the right interface on VM that need to be selected ??

---

### Post by haqking on 2011-10-25
> **theluli said:**
> Hi drdos2006

Thanks for your help , but when l select bridge adapter on VM also under name l have:
br0
eth0
eth1
tap0
vmnet1 -vmware player
vmnet2 -vmware player
vribr0

So when l check the ip and interface on VM machine , a got there eth0 and Lo
So das the eth0 represent dhe host machine or guest machine ????

Yesterday l tried with vribr0 , and it worked , but l am not sure whether is the right interface on VM that need to be selected ??

Bridge to whatever connection you want to use, if your host main LAN and internet connection is on Eth0 then use that, if it is on Wlan0 then use that, depending on what network you want your VM to be.

---

### Post by theluli on 2011-10-25
hi haqking

Thanks for the help

---

