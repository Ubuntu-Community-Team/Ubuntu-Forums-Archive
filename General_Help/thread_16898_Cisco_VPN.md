---
title: "Cisco VPN"
date: 2005-02-24
forum: General Help
---

### Post by jeane123 on 2005-02-24
hi , i need to find out where i can find my kernel source files? I used apt-get to intall my new kernel and i need this to install Cisco VPN client??

Anybody have an idea??

Thank you

---

### Post by Darrena on 2005-02-24
[QUOTE=jeane123]hi , i need to find out where i can find my kernel source files? I used apt-get to intall my new kernel and i need this to install Cisco VPN client??

Anybody have an idea??

Thank you[/QUOTE]
 Look in synaptic for a Kernel-source packages

---

### Post by ember on 2005-02-24
Have a look at Synaptic search function ... you should be able to locate and install linux-kernel-headers-x.y.z ... you should choose the one correspondig to the kernel you run. Normally kernel headers are sufficient for compiling.

---

### Post by jeane123 on 2005-03-03
Ok , so i took the "easy way" as last resort  #-o  and Wow vpnc actually works. For cisco VPN.

Easy and works. 

Just remember the routing ..... or edit the config file

---

### Post by trungkp on 2005-03-08
Hi, I have problem with VPN. Before posting, I did search around the forum.

When I run "vpn_install"

I see the following lines:
./driver_build.sh: line 44: cc: command not found
./driver_build.sh: line 45: cc: command not found
./driver_build.sh: line 46: cc: command not found
./driver_build.sh: line 47: cc: command not found

I think that I did include the kernel headers correctly: /usr/src/linux...
This is the first time I try to use Linux.

Can anyone help me?

---

### Post by Cleaner on 2005-03-11
Hi,

It seems that you are lacking gcc which the installer needs to compile a kernel module. So do a
```
sudo apt-get install gcc
```
and try again. If another "command not found" error comes up, try to install the suitable package as well.

HTH,

Cleaner

---

