---
title: "Ubuntu ZFS on Linux and ISCI oh my!"
date: 2011-10-11
forum: General Help
---

### Post by porkbird on 2011-10-11
Hi All, 

So I have a configuration question that might be based on a completely faulty assumption. So if you have an idea on how this setup could work better please give me a heads up. Otherwise, here is what I am trying to do: 

I have a workstaiton running 10.04 LTE on a AMD Phenom II X6 1100T, 16GB of ram, 5 2TB hard drives 1 60GB ssd. 

I need to use this workstation to run multiple VM's that I can later destroy. I need to have about 15TB of usable space(zfs compression) and it needs to be shared between all of the VM's. But they do not need to see each others data. 

Right now I decided to use Vbox to host my VM's. I cannot use VMware because it does not support the particular hardware I have. I have 1 ssd used for actually running Ubuntu, and then I have the 5 2TB drives mounted via zfs-fuse in 1 pool with 5 different file systems. I am going to rebuild this whole zfs pool with zfs in the kernel instead of running it through fuse, but I have a few more questions. 

Basically I need to know what you guys think would be the best way to share the storage with the Vbox guests. They are going to be a combination of redhat and windows boxes. Up to this point I was using samba, and NFS but both have their limitations and were causing major issues when I tried to run 9 guests all sharing different folders. 

I tried using a shared folder in vbox but that also failed pretty badly, and just giving each VM a very large drive is a no go because then zfs sees just one very large file, > 1TB and tends to corrupt the virtual disk. 

I know this seems complicated, but the reason I am doing this is because I am on an extremely tight budget. I do not have the funds to buy a real server and san to do this work. The one option I have not explored is running the Ubuntu host as just an iscsi target, and then getting another machine with no drives that will host the VM's and mount the iscsi drives. The only think about that is I have never done it, and I have no idea what performance would be like. Also, since you have to share a specific target size I would have to plan exactly how much space each server would need.

Any help, advice, directions to a good psychiatric facility would be appreciated.

---

### Post by dajhorn on 2011-10-12
> **porkbird said:**
> 

Right now I decided to use Vbox to host my VM's. I cannot use VMware because it does not support the particular hardware I have.

What kind of error are you getting during VMware installation?

VMware Workstation should run on this kind of hardware, and its dependent clone feature is a big storage saver.

> **porkbird said:**
> 

Basically I need to know what you guys think would be the best way to share the storage with the Vbox guests. They are going to be a combination of redhat and windows boxes. Up to this point I was using samba, and NFS but both have their limitations and were causing major issues when I tried to run 9 guests all sharing different folders.

I tried using a shared folder in vbox but that also failed pretty badly, and just giving each VM a very large drive is a no go because then zfs sees just one very large file, > 1TB and tends to corrupt the virtual disk. 


The vboxfs driver is probably the best solution, so you should provide more detail on how the Virtual Box Shared Folders feature is failing.  Past that, you're not likely to do any better than NFS over loopback.

Given that both VMware and Virtual Box are broken on this computer, I would double-check the host configuration before doing any complex guest configuration.

The AMD Penom II X6 1100T was released several months after Ubuntu Lucid was published, which could cause problems.  Try a kernel backport or a more recent distro release.

---

### Post by TheR on 2011-10-15
I can confirm that iSCSI with LVM is probably closes to bar metal as it can get. 

I ran 4 300GB Raptors in RAID 10 and get 150MB/s running hdtach in Windows server running on KVM server. Network is 10Gb/s Ethernet.

Disadvantage is as you have already recognized that disk drives are fixed size.

by
TheR

---

