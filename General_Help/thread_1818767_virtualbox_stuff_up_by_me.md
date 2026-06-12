---
title: "virtualbox stuff up by me"
date: 2011-08-05
forum: General Help
---

### Post by cowboy7305 on 2011-08-05
The virtual machine execution may run into an error condition as described below. We suggest that you take an appropriate action to avert the error.
The host I/O cache for at least one controller is disabled and the medium '/home/mine/VirtualBox VMs/mine/mine.vhd' for this VM is located on an ext4 partition. There is a known Linux kernel bug which can lead to the corruption of the virtual disk image under these conditions.
Either enable the host I/O cache permanently in the VM settings or put the disk image and the snapshot folder onto a different file system.
The host I/O cache will now be enabled for this medium.

I deleted Virtualbox and then reloaded it 
have a win7 bootable disk 
iam tolaly lost with the above message 
first time i loaded win7 and used virtual box it loaded ok this time the above message 
any help please

---

### Post by thefasterblueone on 2011-08-05
After checking this out I realize I have the same issue. To resolve it open VirtualBox Manager , highlight a virtual machine, move to the right pane and select 'storage', you will have an 'IDE Controller and a 'SATA Controller', just check the box that says 'use host I/O cache'.

No more error in VBox logs. 

There is more detail in the Vbox help manual.

---

### Post by cowboy7305 on 2011-08-05
no this did not do the trick 
still not loading

---

