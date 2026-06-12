---
title: "Kernel problems after update."
date: 2010-01-04
forum: General Help
---

### Post by stvdel on 2010-01-04
I am using 9.10. I just did an update today which I noticed included a kernel update. It asked me for a restart and I choose to restart. I get an error message now saying:
error: You need to load the kernel first.
Failed to boot default entries.
Press any key to continue...
If I press a key it just loops the same message. Does anyone know how to fix this?

---

### Post by stvdel on 2010-01-04
after running sudo fdisk -lu

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192779       96358+  83  Linux
/dev/sda2          192780   156296384    78051802+   5  Extended
/dev/sda5          192843   156296384    78051771   83  Linux

The way I set up my system was a /boot partition which is the /dev/sda1 and then I set up an encrypted partition and within that I used the LVM to chop it up to make my /, /home, and swap partitions.

I at least want to try to recover some of my files out of my /home that I need but even when I boot the Live CD and go to places to get to my files and then I see my 80GB encrypted LVM partition icon and click to open it up it asks me for the password which I entered and then I get an error saying unable to mount 80GB LVM2 physical volume, not a mountable file system. 

I don't know how to get at my files now or how to find a way to reinstall the boot partition. I don't know if this is a problem with GRUB or the Kernel.

---

### Post by uniquegch on 2010-04-29
Hello everybody,

I got the same problem. I am new with Linux when it comes to indepth troubleshooting skills.I have Ubuntu 9.10 installed with the disk being encryption. 


[LIST=1]
[*]I tried to clone the disk with clonezilla, but it took too long.
[*]When I booted the system I got the message that /boot is full
[*]googled on how to fix that problem
[*]used Synaptic by uninstalling linux-kernel versions. and here I screwed up my system, because I uninstalled active kernel
[*]so of course after I rebooted I got the error message that "you have to load the kernel first"
[*]When I boot using the live CD I can not mount that encrypted LVM2 partition.
[/LIST]
QUESTION: How can I fix the broken grub and get my system back or at least access to my data?

---

### Post by dino99 on 2010-04-29
"because I uninstalled active kernel"

for sure that's stupid :lolflag:

now you have to boot from a cd/dvd or usb which have a ubuntu distro and chroot into your broken lucid installation, run synaptic and reinstall kernel.

follow this example and change with your settings:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

if you think you are unable to do this, the simplest way is to reinstall from scratch.

---

