---
title: "Duel booting with Fedora 16?"
date: 2011-12-01
forum: General Help
---

### Post by ScottishGirl on 2011-12-01
Hello :)


I am currently running Ubuntu 11.10 but I would like to duel boot with Fedora 16.  The the reason for this is I am studying for the Linux system admin' certificate and I would like some experience of using an RPM distro - without having to give up Ubuntu of course!    

Several months ago I formatted my drive with G-Parted and installed Fedora 15, but while my Ubuntu partition was safe I couldn't access it.  Is there a way that I can choose between Ubuntu and Fedora at boot-up?   

At the moment I am only running Ubuntu, so that partition has a bootmanager installed on it.   can I install a boot manager on two partitions?   I don't think that this is possible, but I don't know much about hard drives and partitions.   Thanks.


processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Celeron(R) Dual-Core CPU       T3500  @ 2.10GHz
stepping	: 10
cpu MHz		: 2094.820
cache size	: 1024 KB


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             292G   28G  250G  11% /
udev                  934M  4.0K  934M   1% /dev
tmpfs                 377M  812K  376M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  941M  128K  941M   1% /run/shm

---

### Post by oldfred on 2011-12-01
You can shrink your / (root) with gparted and install Fedora. Some have suggested not to let Fedora use the LVM. It normally wants to install a separate /boot and the main install in a LVM, but during install you can tell it just to install to one partition. You also do not install the grub2 boot loader. Back in Ubuntu a sudo update-grub will find Fedora and let you boot it.

Related threads on multi-booting Fedora with more info:
[http://ubuntuforums.org/showthread.php?t=1888281&highlight=Fedora+16](http://ubuntuforums.org/showthread.php?t=1888281&highlight=Fedora+16)
[http://ubuntuforums.org/showthread.php?t=1885181](http://ubuntuforums.org/showthread.php?t=1885181)

---

### Post by btindie on 2011-12-01
You've got two main options, you can either dual boot or you can install KVM/virt-manager and run it as a virtual machine. Presumeably you just need it as a server? May want to use CentOS as that's closer to RHEL. You can run it headless and then ssh to the VM and use X-forwarding for gui applications for remote admin when needed.

What's the output of:
sudo fdisk -l /dev/sda

You'll need to resize your root partition if you want to dual boot to make space.

Get a copy of PartedMagic and use GParted to resize sda1. You may need to create an extended partition as you can only have 4 primary ones.

If your CPU is up to it, the easier option is to run a VM. You shouldn't notice much int the way of a performance hit.

---

### Post by ScottishGirl on 2011-12-01
> **btindie said:**
> You've got two main options, you can either dual boot or you can install KVM/virt-manager and run it as a virtual machine. Presumeably you just need it as a server? May want to use CentOS as that's closer to RHEL. You can run it headless and then ssh to the VM and use X-forwarding for gui applications for remote admin when needed.

What's the output of:
sudo fdisk -l /dev/sda

You'll need to resize your root partition if you want to dual boot to make space.

Get a copy of PartedMagic and use GParted to resize sda1. You may need to create an extended partition as you can only have 4 primary ones.

If your CPU is up to it, the easier option is to run a VM. You shouldn't notice much int the way of a performance hit.



This is the output of sudo fdisk -l /dev/sda

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   621223935   310610944   83  Linux
/dev/sda2       621225982   625141759     1957889    5  Extended
/dev/sda5       621225984   625141759     1957888   82  Linux swap / Solaris

---

### Post by ScottishGirl on 2011-12-01
I have got GParted and I am downloading PartedMagic at the moment.  I won't be able to re-partition and install Fedora until Saturday so I will tell you then how I got on.

Thanks for your help guys.  :D

---

### Post by btindie on 2011-12-01
> **ScottishGirl said:**
> This is the output of sudo fdisk -l /dev/sda

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   621223935   310610944   83  Linux
/dev/sda2       621225982   625141759     1957889    5  Extended
/dev/sda5       621225984   625141759     1957888   82  Linux swap / Solaris

If you want to dual boot you'll have to change your partitions, running Fedora as a VM you can leave them alone.

You'll need to shrink the Linux partition, sda1, grow the Extended partition to fill the new space and finally create a new Linux partition for Fedora. You can then have Ubuntu boot into Fedora if you get it to install grub into the install partition and not the MBR.

---

