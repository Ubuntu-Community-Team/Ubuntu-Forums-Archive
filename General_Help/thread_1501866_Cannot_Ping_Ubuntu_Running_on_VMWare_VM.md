---
title: "Cannot Ping Ubuntu Running on VMWare VM"
date: 2010-06-04
forum: General Help
---

### Post by 808mlee on 2010-06-04
Hi:
 
I just completed clean install of Ubuntu Linux 10.04 to run Nagios. I have Nagios up and running properly and monitoring my windows servers. I have a couple of questions that I can't seem to find the answer to:
 
1. I cannot ping the Ubuntu VM from other machines on the same subnet. I can ping the Host system from other machines on the same subnet. I can also log on to the Ubuntu VM and ping all other machines on the local subnet. I can also ping the Ubuntu VM from the VMWare host system.
 
2. I have installed apache and the Nagios software is running correctly but I can't use a web browser to attach to the Nagios web page from other machines on my local subnet. I wonder is this is related to my inability to ping the Ubuntu Linux machine.
 
Some things I have tried:
 
1. Disable IPV6
2. Check to make sure firewall is turned off. I ran iptables -L and see no rules
 
I don't know what else to do at this point. Any help you can provide will be greatly appreciated.
 
Thanks.
 
Mark Lee

---

### Post by dcstar on 2010-06-04
> **808mlee said:**
> Hi:
 
I just completed clean install of Ubuntu Linux 10.04 to run Nagios. I have Nagios up and running properly and monitoring my windows servers. I have a couple of questions that I can't seem to find the answer to:
 
1. I cannot ping the Ubuntu VM from other machines on the same subnet. I can ping the Host system from other machines on the same subnet. I can also log on to the Ubuntu VM and ping all other machines on the local subnet. I can also ping the Ubuntu VM from the VMWare host system.
.........

[LIST=1]
[*]Please post all VM questions in the Virtualization forum
[*]Only Bridge networking on VMs will allow access from other nodes.
[/LIST]

---

