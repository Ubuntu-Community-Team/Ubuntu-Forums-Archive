---
title: "Tool to eject external LVM disk"
date: 2011-12-21
forum: General Help
---

### Post by jartsa on 2011-12-21
*This post describes a tool which can be used to eject LVM governed external hard drives.*

**Problem**:
I have an external hard drive as a backup disk, but it is governed by LVM, and one partition is even encrypted via LUKS. My problem was that it was very tedious to manually unplug the disk from the kernel with all the overlaid systems active.
 
Therefore, I have written a tool to solve my problem. If there are other people with similar setup, you may find the script useful. So:
 
**Description of the setup**:
You have an external hard drive, which you want to hotplug (via usb, eSATA, something else) and later remove, for example to use it for backups. However, it is governed by the LVM and possibly LUKS, so only unmounting the partitions will not suffice, but also the encrypted partitions must be closed and the logical volume group removed from the kernel, as well as the physical disk itself.
 
**Solution**:
The script lvmeject inspects your setup, and takes appropriate actions to unmount partitions on the volume group, close encrypted volumes and remove the volume group from use. If there was also normal partitions on the physical disks that were hosting the VG, they will also be unmounted and locked. It also spins down the external disk and ejects it from the system, so you can unplug the external disk from your system.
 
So, the tool takes volume group as an argument and at the end that volume group is gone from the kernel, as well as other partitions from the external disk, so you can unplug the disk from your system safely.
 
I have tested it with a couple of setups, including one where LVM was spanning two external disks (eSATA hard drive and an usb-stick) and had LUKS encryption both below and above the LVM.
 
You can download this tool from launchpad. I've setup a repository with ubuntu package. It contains the script and a man page. The ppa-repository can be found from: [https://launchpad.net/~yartsa/+archive/lvmeject](https://launchpad.net/~yartsa/+archive/lvmeject). You can add the repository to your system using 
```
sudo apt-add-repository ppa:yartsa/lvmeject
```

and install the package
```
sudo aptitude install lvmeject
```

The package contains just the script and the man page, which will be installed to appropriate locations. Some examples and explanations are at the man page: man lvmeject
 
You can also dowload the source script from the project page: [https://launchpad.net/lvmeject](https://launchpad.net/lvmeject). The advantage of using the repository is that apt should pull all the dependencies with the deb, in case some of the tools are missing in your system (which is unlikely, if you already have a setup which requires this tool).
 
I hope that this will be useful for people, who want to use the flexibility of LVM and encryption power of LUKS also on their external disks.
 
I more than welcome you to contribute and enhance the script! I appreciate all feedback and test results, as well as any suggestions.

---

