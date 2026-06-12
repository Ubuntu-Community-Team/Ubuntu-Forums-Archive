---
title: "Grub Error 18: Selected cylinder exceeds max supported by BIOS after Ubuntu Upgrade"
date: 2011-04-02
forum: General Help
---

### Post by steve3742 on 2011-04-02
[FONT=Arial][SIZE=2]Hi, I run Ubuntu 10.04 on quite an old machine and I update it pretty much automatically. The last three kernel upgrades have returned a Error 18: Selected cylinder exceeds maximum supported by BIOS from Grub[/SIZE][/FONT][FONT=Arial][SIZE=2] every time I boot up. I'm able to use the older kernel (Ubuntu 10.04.2 LTS, kernel 2.6.32-27-generic, the 7th one down in the Grub Menu - it's got lower as the number of kernels with this error has increased), but I can't boot into the current kernel (currently Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic.)[/SIZE][/FONT][FONT=Arial][SIZE=2]

OK, sudo fdisk -lu gave me the following:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000673b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306568394   153284166   83  Linux
/dev/sda2       306568395   312576704     3004155    5  Extended
/dev/sda5       306568458   312576704     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79d86c54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   154079414    77039676   83  Linux
/dev/sdb2       154079415   160071659     2996122+   5  Extended
/dev/sdb5       154079478   160071659     2996091   82  Linux swap / SolarisAnd sudo gedit /boot/grub/menu.lst gives the following list:
> title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro  single
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-29-generic
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-29-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.32-29-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-29-generic (recovery mode)
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-29-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro  single
initrd        /boot/initrd.img-2.6.32-29-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.32-28-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro  single
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-27-generic
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.32-27-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro  single
initrd        /boot/initrd.img-2.6.32-27-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-26-generic
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid        d45f9637-0c9d-4f4f-8515-8a80291e93bc
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=d45f9637-0c9d-4f4f-8515-8a80291e93bc ro  single
initrd        /boot/initrd.img-2.6.32-26-genericThis is only the first 10 - it carries on, but the 7th onwards are bootable.

Can anyone help with this? I can't see why I'm getting an Error 18 only on the more recent kernels (this did happen before and the problem corrected itself on the next kernel upgrade.)

Thanks[/SIZE][/FONT]

---

### Post by dandnsmith on 2011-04-02
I'd guess that the area where the kernels/initrds are placed is critical for you. Facing this problem a while back, I had, by good fortune, a ready solution - to get the files within reach of the modules.
I was fortunate in that I'd opted a good while back to have a seperate boot partition, and I just copied the out-of-reach modules into this and modified the boot entries accordingly.

I don't know whether this helps you.

---

### Post by steve3742 on 2011-04-02
Hi dandnsmith
This had occurred to me - I've been googling for solutions and one of them mentioned putting Grub into a separate boot partition. But how easy would it be to create a boot partition without erasing all my current partitions? It has to be at the beginning of the disk, I believe, the first 1072 cylinders. And that area is already taken up. I've resized partitions before, but from the end, not the beginning. Is this doable? Is it easy to do? Is it fraught with dangers that could make my whole system unusable if I get it wrong?

---

### Post by dandnsmith on 2011-04-03
It's feasible.
I'd make sure I had a copy of the partition(s) to be affected first (see posts somewhere on using rsync so as not to copy the whole lot).
I don't know whether gparted would do the job (with the partition in question not mounted - liveCD?), but it's worth a try.
Otherwise format the partition, and then squeeze it, followed by a restore.
You might have to do something about partition numbers, as they might get out of order - don't know if gparted copes with this automatically (I would hope so, but haven't checked it out)

Good luck

---

### Post by steve3742 on 2011-04-25
[FONT=Times New Roman][SIZE=2]I was contemplating doing what was suggested here, but thinking of just backing up all my data and doing a complete new install of Ubuntu 11.04 instead, once it's released (I tend to do this every year or two anyway.) However, I found another way whilst searching the internet. Basically, I used Synaptic to remove all my Linux kernel images bar the one that worked (having used [/SIZE][/FONT][FONT=Courier New][SIZE=2]uname -r[/SIZE][/FONT][FONT=Times New Roman][SIZE=2] to find the version number - 27) and the latest one (31.) I then reinstalled the latest one using Synaptic again and used [FONT=Courier New]sudo update-grub[/FONT] to update grub (probably not necessary as Synaptic had probably done it already.) I rebooted and it worked fine, booted into version 31 with no problems. I think I'll keep my old kernel images down to 2 or 3 from now on. (I've freed up nearly half a gig of space also, another reason for doing this.)

Anyway, I thought I'd post back to say that I've solved the problem, to thank you for your help and to mark the thread as having been answered (assuming I can work out how to do that - I'm a bit of a newbie here.) It might also help other people having the same problem.[/SIZE][/FONT]

---

