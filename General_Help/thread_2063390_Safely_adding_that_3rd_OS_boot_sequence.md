---
title: "Safely adding that 3rd OS boot sequence"
date: 2012-09-27
forum: General Help
---

### Post by allen76693 on 2012-09-27
I recently upgraded to 12.04 just to enjoy benefits of more recent version of virtualbox. I have attempted to install from snyaptic as well as direct from oracle and via terminal. Just giving you background for only reason I want VB is load my 3rd Linux OS.
Look at attachment (do not laugh gparted not my strong suit):confused: 
If I changed one of those fat32 to ext4 is there a sure fire way I would have a multiple boot sequence. If so tell me how or direct me to a resource. The OS in question is SUSE 12.1. I thank you in advance and if you did not laugh at my partitioning efforts I thank you as well. You too may be 81 some day:lolflag:

---

### Post by mdurham on 2012-09-27
I don't think that you can multi-boot into Virtual Box. You must boot into the OS containing VB, then, boot into the VB system.

---

### Post by Rexilion on 2012-09-27
I think that allen wants to:

- Have another Linux partition containing Suse 12.1 and be able to boot that distribution directly
- Use VirtualBox in Ubuntu to also boot that same Suse 12.1 in a virtualized environment

I think this should be possible with Linux since it's kernel automatically detects the appropiate drivers at boot. This is not possible with Windows though because of HAL...

Is this what you wanted?

I want to make a remark about your partition table (NOT your skills). It seems that something is making unnecessary holes between every partition. What software did you use to partition your system??

---

### Post by allen76693 on 2012-09-27
You are correct I want to be able to conveniently multiple boot between Ubuntu, Dreamlinux, and Suse, but I fear I will lose my boot sequence and end up only Suse and have to start over.


I used gparted and I have no clue why those holes happen. In past when I was booting windows and Linux the same thing happened. So is there a tip or clue whereby I can install Suse into a multiple boot. I thank you for your reply

---

### Post by Rexilion on 2012-09-27
It depends on two factors actually:

- Is the Suse installer smart enough to detect other OS's correctly?
- Where do you point Suse to install it's bootloader?

If I would have multiple distro's I would:

- Make a master GRUB booter
- Let each distribution install their MBR inside their OWN partition (with bootloader)
- Chainload each distribution specific bootloader with the master bootloader

This has the advantage of you not having to maintain a bootloader which keeps all three operating system's accessible.

You have an SSD disk btw??

---

### Post by allen76693 on 2012-09-28
The master grub booter is a great innovation and I thank you.
Granted one can just take a peek as it were by using virtualbox, but I decided to put the master boot partition to supreme test and I now have Fedora 17, Suse 12.1, Dreamlinux 5 and Ubuntu 12.04 in a comfortable boot sequence. Again my thanks.

---

