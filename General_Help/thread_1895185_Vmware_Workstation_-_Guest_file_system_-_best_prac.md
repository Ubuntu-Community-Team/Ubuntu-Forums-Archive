---
title: "Vmware Workstation - Guest file system - best practices"
date: 2011-12-14
forum: General Help
---

### Post by swappa on 2011-12-14
Hi there

Xubuntu 11.10 x64. / 3.0.0-14-generic  

VMware workstation 8.0.1
Virtualbox 4.1.6 

I am currently experiencing poor disk I/O performance on my Windows7 guest. The file system used for my VM is NTFS (SSD drive) since it is being shared between my Linux and Windows installs. Virtualbox outperforms VMware by far, but I feel that it isn't good enough compared to how my VM's perform opened up in Windows instead of Linux.

I am contemplating re-formatting this drive to something that would provide better I/O performance. Question is; what linux file system would that be? It is not necessary for Windows to see this partition. I am after the best performance possible. 

I have googled a bit back and forth, but I get mixed answers. Maybe it isn't a filesystem issue so much as a SSD/Linux kernel problem?

---

### Post by swappa on 2011-12-15
Reformatted the SSD drive to use XFS. 
I have much better I/O performance now, and the whole computer just feels faster. On the VM I can actually start an AV scan without having to stop whatever it is I am doing on the host. 

I am aware of the risks with XFS, but I keep regular backups of my VM's, so I am willing to take that chance.

---

