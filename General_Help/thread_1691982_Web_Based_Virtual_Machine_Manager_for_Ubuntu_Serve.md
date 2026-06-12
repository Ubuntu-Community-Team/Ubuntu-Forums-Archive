---
title: "Web Based Virtual Machine Manager for Ubuntu Server"
date: 2011-02-20
forum: General Help
---

### Post by FeraTech on 2011-02-20
Are there any open source Virtual Machines which have web based administration.

I am setting up Ubuntu 10.4 x64 and would really like to find a usable virtual machine manager.

I really like Virtualbox but only the full version has web based administration.

I have also tried VMware but it isn't open source.

Anybody have any suggestions?

---

### Post by Syed75 on 2011-02-20
[https://fedorahosted.org/ovirt/](https://fedorahosted.org/ovirt/)

[http://virt-manager.et.redhat.com/](http://virt-manager.et.redhat.com/)

[http://book.opensourceproject.org.cn/distrib/ubuntu/8.04/serverguide/C/libvirt.html](http://book.opensourceproject.org.cn/distrib/ubuntu/8.04/serverguide/C/libvirt.html)

---

### Post by FeraTech on 2011-02-20
Ovirt
- this doesn't seem like it's even been tested most of it's own website doesn't work and there aren't any build instructions for ubuntu

Virt-Manager
- This isn't web based.

Libvirt
- Requires a GUI or is text based.

None of these offer web based management...

---

### Post by iclebyte on 2011-02-25
As far as I am aware, there are only 2 real players in the opensource web based virtual machine management area.

These are: 

Convirt 2.0 - [http://www.convirture.com/products_opensource.php](http://www.convirture.com/products_opensource.php)
Convert it written in Pyhton, and in all honesty, it's quite good. I've been testing it over the last 2 weeks using Openfiler as an iSCSI SAN and it works quite well. I do find it a little clunky and it has this 'closed box' feel to it - but that maybe because it's written in Python and I don't know it. Convirt is very much like VMWARE Server, I think it's trying to be like the VMWARE VSphere. However alot of the cool features like live migration and automatic placement of VM's seems to only be in the enterprise version which I don't like very much.

OpenQRM - [http://www.openqrm.com/?q=node/2](http://www.openqrm.com/?q=node/2)
OpenQRM is a 'datacenter management platform' - Don't be fooled by their website, it's basiclly a web based virtual machine provisioning system (which is what you want). However it has some other rather cool features. It can manage physical boxes too, probably the coolest feature is that it can suck up a physical machine and create a virtual one out of it. However, the documentation is not very good, so far the forums have not managed to answer my questions either. On the other hand, the web interface is brilliant, and it's written in PHP. One thing I don't like is that (as far as I can tell) in order to use anything as a resource you need to be running an OpenQRM-Client package - now I'm trying to attach an Openfiler iSCSI target and as far as I'm concerned I should not have to run any clients on the SAN in order to do this. So far I am yet to get OpenQRM to work properly which is a shame because my evaluation period will be coming to an end soon and I'd probably rather go with this product as it seems more stable for a production environment.

The bottom line is there doesn't really seem to be anything which is simple, open and cool. Every project which starts something seems to realise their on to something big and tries to monatize it.

---

### Post by edbz on 2011-02-25
not sure what u want, why not try webmin/ webadmin. i once usedit on 10.4 server. u just need to select it when installing.

---

### Post by FeraTech on 2011-02-25
Webmin is not able to control virtual machines on a system.

Any idea how to configure:
convirture-tools

It seems like the installation guide is designed for a multiple server installation and I am having trouble setting it up on one. The strange part is that convirture-tools is in the repository. However, the guide requires running scripts from convirture-tools and I am not sure where to proceed.

---

### Post by justin007827 on 2011-07-13
iclebyte, 

I am trying to get convirt working with openfiler and am having a hard time.  Would you be able to point me to any documentation or explain the process you went through to get it working?

I was able to connect it via the "manage storage" action, but it says the size is "0." and I am not sure how I designate this as a storage device when creating new VMs. 

Thanks in advance, 

Justin

---

### Post by JedMeister on 2011-07-13
I think this is what you are after:
[http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

There is a patch constructed for Turnkey Linux here: [http://www.turnkeylinux.org/forum/general/20110212/tklpatch-virtualbox-headless](http://www.turnkeylinux.org/forum/general/20110212/tklpatch-virtualbox-headless)
As TKL is based on Ubuntu 10.04/lucid you should be able to create an install script from the instructions pretty easy.

---

### Post by justin007827 on 2011-07-13
I'm definitely not looking for an interface to virtualbox. virtualbox is great for desktop virtualization, but I need a multi-node server environment with a SAN device for shared storage.

---

### Post by JedMeister on 2011-07-14
Sorry I misunderstood. 

In that case I would strongly recommend [ProxmoxVE]("http://www.proxmox.com/products/proxmox-ve"). It is a very cool Debian based hypervisor. 

One great advantage IMO is that it utilises KVM and OVZ so Linix servers run like on hardware in OVZ containers and other OS (or Linux too if you wish) run close to bare metal performance in KVM (especially if you install the oVirt drivers). It has facility for backing up live VM servers and can also be clustered with VMs able to be migrated from one hardware node to another seamlessly (or so I've heard I haven't actually tried that feature).

---

