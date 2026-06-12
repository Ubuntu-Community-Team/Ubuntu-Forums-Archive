---
title: "vmware would not start network in promiscuous mode"
date: 2009-08-10
forum: General Help
---

### Post by sefs on 2009-08-10
Hi all,

I am having a problem where vmware would not start the guest os with the network interface in promiscuous mode.

The fix is to create a new group, say "vmware-vmnet0"

Add the user who is running vmware to this group, and then set the group of /dev/vmnet0 to vmware-vmnet0 and ensure that that group has read/write permissions for /dev/vmnet0.

This all works until I reboot my system, where then ubuntu takes it upon itself to revert my settings on /dev/vmnet0  to owner:root, group:root. 

How can I stop this very bad behaviour.

Thanks.

---

### Post by sefs on 2009-08-10
from a vmware guru...
---
"Device nodes are recreated at boot time. You can thank Linux udev. To work around this, create the vmnet* devices with the ownership and permissions you want under /lib/udev/devices."
---
How do I go about doing this?

Thanks.

---

