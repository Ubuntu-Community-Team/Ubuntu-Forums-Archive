---
title: "Multiple OS on 1 PC Hardware"
date: 2011-08-18
forum: General Help
---

### Post by dvanwijk on 2011-08-18
Hi,
I have been experimenting with Linux for a little while but still class myself as a newbie.

I work for a technology company manufacturing PDA's.

We want to setup a test environment of multiple PC configurations (Linux, Mac, Windows - XP, Vista, 7 and both 32 and 64 bit platforms).

I have played with GRUB a little and got that working with Windows XP Pro for dual boot options on Ubuntu.

I am wondering if it is possible to setup more operating systems on the 1 computer hardware (could install more hard drives if required) with GRUB. Not sure if PC hardware can take installs of both 32 and 64 bit platforms or not.

Or is it better to have 1 PC for each OS? What are the advantages of that? Obvious disadvantage is cost of hardware.

Or is it better to setup VirtualBox for this sort of environment?

Any advice or recommendations about how to approach this would be gratefully received.

Thanks,
Dan

---

### Post by angry_johnnie on 2011-08-18
multi booting is perfectly possible.  grub is pretty good at handling that.  as far as how many systems can be installed, it all depends on how much space you have on your hard drive, and also, whether the systems you are installing must be installed on a primary partition, or whether they want to be installed on the first partition of the hard drive (ms dos does that, for example).

as far as running 64 and 32 bit systems, it is also possible, as long as you have a 64 bit machine.  it will handle 32 bit systems with no problem.

installing windows and linux should be the easy part.  mac... not so much.  legally, you can only install mac osx on a mac.  you could try one of the osx86 builds, which are hacks, not supported, and yes, illegal, so you won't get support for that in this forum.

if your systems require a primary partition, you'll need more drives, but that should be the only limitation.

it would be easier if you install the windows os's first.  xp first, 7 last.  the windows 7 bootloader should be able to handle any older versions of windows.  after you have that settled, you can install linux, which will add a windows loader to grub, from which you can select the different versions of windows.

---

### Post by dvanwijk on 2011-08-19
Hi angry_johnnie,
Thanks for your reply. What software (if any) would I use to facilitate this? Or does the Windows installer take care of it all?

Regarding Mac, I'll just accept that we need separate hardware for it.

With regard to primary drives, do you happen to know which systems require to be setup on primary drives? I don't really understand the concept of primary drives so I am hoping you can advise. I don't mind getting more hard drives as they are quite cheap - just need to make sure the PC I buy will have enough available IDE/SATA slots.

I assume I'll need to purchase full versions of Windows licenses (not OEM)?

The purpose of my setup is to provide our customers with telephone and email support for our PDA with their OS (installing drivers, software, etc)

Also, I am not sure if VMWare is more suited to what we are trying to achieve or not.

Thanks very much for your help.

Regards,
Dan

---

### Post by angry_johnnie on 2011-08-19
vmware would be quicker, but virtualized hardware is not the same.  not if you're actually installing the drivers, at least.  if you just want to see what your customers are seeing so you can guide them, then probably a virtual machine would be better, since you would be able to quickly access any system without having to re boot.

as far as partitions go, your hard drive can only have 4 primary partitions.  so if your systems require a primary partition to be installed on (i'm pretty sure windows *wants* a primary partition), you'd be limited to 4 systems per drive.

linux systems can easily dwell in an extended partition.

[here]("http://en.wikipedia.org/wiki/Disk_partitioning") is some info on partitioning.

[gparted]("http://gparted.sourceforge.net/"), which is included in the ubuntu installation cd, is probably the best tool to partition a hard drive.

you can use your windows installation disks to take care of the windows partitions, but windows cannot create, or modify, a linux partition.

but, then again, if you just want to see what they see, a virtual machine is probably a lot easier, and quicker.

as far as virtual machines go, you do have options

[virtual pc]("http://www.microsoft.com/windows/virtual-pc/") (for windows)

[boot camp]("http://www.apple.com/support/bootcamp/") (for mac - not really a virtual machine, but if you want to purchase apple hardware this is what you would use to install other os's)

[virtualbox]("http://www.virtualbox.org/wiki/Downloads") (multi platform)

[vmware]("http://www.vmware.com/") (multi platform)


i'm pretty sure there's more options, but these are the most common.

---

### Post by walt.smith1960 on 2011-08-20
I use a commercial boot manager that will support over 100 operating systems, each running in its own primary partition.  When installing only that one partition is "seen".  You can set each OS up to see other partitions depending on what you want.  If you google "terabyteunlimited" you'll find it.  BootitBM has its peculiarities but it can control a LOT of different operating systems depending on hard drive size.  It can also work with more than one hard drive.  I don't know how it'll work with non-BIOS systems; I suspect not well.

---

