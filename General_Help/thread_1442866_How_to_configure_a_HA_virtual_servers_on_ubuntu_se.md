---
title: "How to configure a HA virtual servers on ubuntu server with windows VMs"
date: 2010-03-30
forum: General Help
---

### Post by rc.dantes on 2010-03-30
Hi good day

I have a project in school that the requirement is to show the proof of concept of a high availability virtual servers. the guest operating system for the test case will be a Windows variant and a Linux variant that if the main host that hosts both of this VMs fails, both VMs will be restarted on the backup host. Simple enough with VMware vSphere and citrix xenserver with essentials with their enterprise features, But I am not allowed to use a software that one will need to pay-for or is only a trial version, i need to use an open source solutions, and i am not allowed to use virtualbox.

the school has provided me 2 server class 64bit hardware with intel-vt support, i have my laptop for management tools and to also run a virtual appliance for a iscsi target (openfiler as a vm in virtualbox in my laptop).

I have figured that i will use KVM on a ubuntu server as my hypervisor but i cant find any how-to on how to implement a high availability setup that will run a windows variant as a guest. can some one give me a step by step on how to do this.

from my research it looks like i will need DRBD and heartbeat, but i dont know how to use them and if they are applicable in my needs. I wouldn't probably use DRBD since I have a sudo SAN with my iscsi  target, so i can probably use open-iscsi. 

Please if some one is kind enough to show me to the right direction of a step by step guide on how to do this.

---

### Post by Aubergines on 2010-03-30
take a look at [http://www.proxmox.com/cms_proxmox/en/virtualization/proxmox-ve/proxmox-ve-startseite.html](http://www.proxmox.com/cms_proxmox/en/virtualization/proxmox-ve/proxmox-ve-startseite.html)

---

### Post by rc.dantes on 2010-03-30
I have already checked out proxmox but sadly high availability is not included and in ther road map will only be added on version 2.xx. i have heard of people saying using drbd with heartbeat will work but its more theoretical on their end, and for me there is no guide to set it up.

---

### Post by fritoss007 on 2010-08-13
how did your project end up ?

---

