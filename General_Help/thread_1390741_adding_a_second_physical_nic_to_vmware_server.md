---
title: "adding a second physical nic to vmware server"
date: 2010-01-26
forum: General Help
---

### Post by Mia_tech on 2010-01-26
guys, I installed vmware server 2.0 and I'm trying to add my second nic card to vmware, so I ran vmware-config.pl, but I'm getting this message
> 
sudo /usr/bin/vmware-config.pl
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmmon
vmnet
vmci

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.


any help appreciated

---

