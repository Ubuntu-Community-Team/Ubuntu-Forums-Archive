---
title: "pci video card on 9.04"
date: 2009-07-24
forum: General Help
---

### Post by dawnlove on 2009-07-24
I have found this in my search to get my GeForce 8400 GS old pci video card working I found this
  [http://ubuntuforums.org/archive/index.php/t-615381.html](http://ubuntuforums.org/archive/index.php/t-615381.html)
but     sudo dpkg-reconfigure xserver-xorg     only sets up key board?? I read 9.04 does things different?

there is no hardware manger in xubuntu so I used terminal command 

dove@dove-desktop:~/Desktop$ sudo lshw -C display[sudo] password for dove: 
PCI (sysfs)  
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GeForce 8400 GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0


so question how do I get the  sudo dpkg-reconfigure xserver-xorg   configured to go to  bus info: pci@0000:05:00.0

any help would be great -thanx

---

### Post by t4thfavor on 2009-07-25
I had an 8400 GS, it was pci-Express. Are you sure yours is PCI?

---

### Post by dawnlove on 2009-07-25
Yes I'm sure its old pci. it works for bios just as a ati rage 128 pci card does. the problem is as in link. I got it cheap because it was old pci. thanx for respond

---

