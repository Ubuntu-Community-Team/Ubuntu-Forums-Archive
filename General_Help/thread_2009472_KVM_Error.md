---
title: "KVM Error"
date: 2012-06-24
forum: General Help
---

### Post by hashval on 2012-06-24
Hello Everyone

        I am running Virtualbox software on my MAC OS LION. On the VirtualBox, I am running the Ubuntu 12.04.  I am trying to boot three nodes using KVM on the Ubuntu 12.04.

When I try to boot a node, I get the below reply and it takes a long time
to boot even the first node and finally it hangs.

root@harsha: /home/harsha/Downloads# Kvm -m 512
-net nic,macaddr=00:00:00:00:cc:10
-net tap,script=/etc/ovs-ifup,downscript=/etc/ovs-ifdown
-cdrom /home/harsha/Downloads/ubuntu-12.04-desktop-amd64.iso
Could not access KVM Kernel Module: No such file or directory
failed to initialize KVM: No such file or directory
Back to tcg accelerator.

Do I need to enable the virtualization on my MAC OS LION  or on the virtual
box which is running Ubuntu 12.04.....Can I get some inputs on this please.

---

