---
title: "So disappointed in Linux KVM!"
date: 2010-07-31
forum: General Help
---

### Post by RMuscaritolo on 2010-07-31
Hey Guys,

I'm hoping you could help point in the right direction or at the least validate my issues...

After having pretty good experiences with ESX 4.0 and now ESXi. I figured why not give KVM a shot?

So to start off, I loaded 64bit Fedora 13 and installed KVM. First thing I notice is that KVM IS NOT actually loading... looks like my Dell Optiplex 760 does not support it so I'm stuck with Qemu... ok, fine worth a shot anyway...

Now, after fumbling around with the Virtual Machine Manager for an hour or so, I created my own VM network and setup a couple new VM storage partitions. Not too bad, except that I had to use NAT for the network because setting up a bridged network was WAY too much trouble than it was worth!

Later after a flawless install of Windows 2003 server from the ISO, the first thing I see on the initial boot from the harddisk is a "disk read error".... I tried a few different options and still had that same issue. Making booting a Windows OS impossible.

After looking into it more, it seems this is a common issue without any real soluton?! How is the open-source competitor to VMWare and Hyper-V NOT support windows VMs? I obviously have to be missing something here...

Is this just a problem with Qemu and me not using true KVM?

I'm not giving up yet, but holys****, you could setup a true VMWare virtual environment in less than 10mins. If anyone has any ideas or pointers for a Linux Noob like me, please let me know!!

Thanks!

---

### Post by JustinR on 2010-07-31
Try VirtualBox or something else other than KVM and Qemu.

---

### Post by RMuscaritolo on 2010-07-31
> **JustinR said:**
> Try VirtualBox or something else other than KVM and Qemu.

Yeah, I think I may have to. It just looks like KVM is a little too advanced for me at this point.


BTW, for anyone interested, this seemed like a pretty fair comparison between the major desktop virtualizations out there right now...

[http://www.linuxjournal.com/magazine/virtualization-shootout-vmware-server-vs-virutalbox-vs-kvm](http://www.linuxjournal.com/magazine/virtualization-shootout-vmware-server-vs-virutalbox-vs-kvm)



Thanks!

---

### Post by randumnumber on 2010-08-01
I use Virtual Box, windows 2000 windows xp and everything i have ever put on it works flawlessly.

---

### Post by Dustin2128 on 2010-08-01
yes, virtualbox is currently the way to go for virtualization.

---

### Post by dcstar on 2010-08-01
> **RMuscaritolo said:**
> 
........
I'm not giving up yet, but holys****, you could setup a true VMWare virtual environment in less than 10mins. If anyone has any ideas or pointers for a Linux Noob like me, please let me know!!

Thanks!

The Virtualization forum is full of information on VMs, and that is where all VM issues should be.

---

