---
title: "Dual boot ubuntu with gentoo"
date: 2006-03-27
forum: General Help
---

### Post by mxa055 on 2006-03-27
Hi,

I have Gentoo linux running on my PC on an 80GB hdd and I have an unused partition (had left it intentionally since gentoo's installation) that I would like to use for Ubuntu (hda4 around 40GB).
I would like some guidance on how I should tackle this as loosing my Gentoo installation from a silly mistake would be a major pain, as it has taken me hundreds of hours to get it to current state (lots and lots of compiling ](*,) )


Thanks

PS: I have experience in installing Ubuntu alone and after Windows but never done it after installing another distro first.

---

### Post by dragonfyre13 on 2006-03-27
Same way as with Windows. Just make sure to click manual partitioning, and set your mount partition as /mount.

---

### Post by jbennett on 2006-03-27
[QUOTE=dragonfyre13]Same way as with Windows. Just make sure to click manual partitioning, and set your mount partition as /mount.[/QUOTE]


Hi, I would like to do something similar to this as well (I am currently dual-booting Windows and Ubuntu, and I would like to add another; perhaps Kubuntu or FC5).  I have approx. 20GB of unpartitioned space on my hard drive, so when I choose to manually edit the partitions, I just create a new partition and mount it at /mount?  Also, do I need to edit GRUB in Ubuntu before I will be able to boot the new distro?  Any help is greatly appreicated.

Thanks

---

### Post by dragonfyre13 on 2006-03-28
Create a new partition, and mount it as / in the new OS. Then, mount the boot partition as /mount. When you finish that, you will most likely have to edit grub, though it very well may work to simply run grub-update. That updates grub to include all the operating systems on the machine. When you install the OS, make sure specefy that you already have grub boot loader installed. Otherwise, it is exactly the same as any install.

---

### Post by jerrykenny on 2006-03-28
MXA,

The biggest risk to your gentoo partitons is making a mistake at the partitioning stage of the ubuntu install . . . . 

At the partitoning stage in the install, you must go for "manual partitoning" which I think has the subtitle "for experts". . . . 

If you're sharing a home partition, make sure the option to format the partition is not checked. . . .

Safest booting strategy would be to sequentially boot , ie dont install Ubuntu's grub to the mbr, install it to the root (or boot if you have one) partition for ubuntu.

Then, you can boot back into Gentoo, edit your /boot/grub.conf file, and add the grub entry for chainloading ubuntu.

I wouldn't have gentoo booting ubuntu directly, as when you get a kernel update from ubuntu, your gentoo grub wont find the new kernel.

If you're paranoid about losing your gentoo installation, then the biggest threat is probably making silly mistakes at the partitioning stage, I always make a graphical representation of my partiton tables using Open Office Draw, and have it there in front of me.

---

