---
title: "How to Uninstall VMware Player 3.0"
date: 2009-12-25
forum: General Help
---

### Post by emoguitarist06 on 2009-12-25
I'm running 32-Bit Ubuntu 9.10

I downloaded VMware player through their website. Which of course required me to make an account. Anyways I downloaded the ".bin" file and installed with:
 "sudo ./VMware-Player-3.0.i386.bundle"
But now I hate it and I'm just going to stick with VirtualBox which I love!
Anyways VMware Player isn't in synaptic package manager or ubuntu software center.

---

### Post by hyperdude111 on 2009-12-25
From google so I'm not 100% sure.

sudo apt-get remove vmware-player

---

### Post by emoguitarist06 on 2009-12-25
> **hyperdude111 said:**
> From google so I'm not 100% sure.

sudo apt-get remove vmware-player

> pumpkinfeet@phillip-laptop:~$ sudo apt-get remove vmware-player
[sudo] password for pumpkinfeet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware-player

but I did this instead:

> pumpkinfeet@phillip-laptop:~$ sudo apt-get remove vmware*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting xserver-xorg-driver-vmware for regex 'vmware*'
Note, selecting vmware-view-open-client for regex 'vmware*'
Note, selecting xserver-xorg-video-vmware for regex 'vmware*'
Note, selecting vmware-package for regex 'vmware*'
The following packages will be REMOVED:
  xserver-xorg-video-all xserver-xorg-video-vmware
0 upgraded, 0 newly installed, 2 to remove and 24 not upgraded.
After this operation, 180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161718 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-vmware ...
Processing triggers for man-db ...

But it's still installed :(

---

### Post by dcstar on 2009-12-25
> **emoguitarist06 said:**
> I'm running 32-Bit Ubuntu 9.10

I downloaded VMware player through their website. Which of course required me to make an account. Anyways I downloaded the ".bin" file and installed with:
 "sudo ./VMware-Player-3.0.i386.bundle"
But now I hate it and I'm just going to stick with VirtualBox which I love!
Anyways VMware Player isn't in synaptic package manager or ubuntu software center.

Look in the Virtualization forum (where all VM questions should be).

---

