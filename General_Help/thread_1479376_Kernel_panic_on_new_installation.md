---
title: "Kernel panic on new installation"
date: 2010-05-10
forum: General Help
---

### Post by lidewei on 2010-05-10
I decided to try Kubuntu (10.4 64bit) again today, it's been a few years since I last tried it. The installation went well, but now I don't seem to be getting past Grub. I get a message that says: Kernel panic - not syncing:VFS:Unable to mount root fs on unknown block(0,0)

I tried to use the recovery mode option in grub but that gave me the same message.

Anyone have some tips on how to fix this? I'm at loss....

---

### Post by lidewei on 2010-05-11
*bump* Anyone?

---

### Post by Joelbruce on 2010-05-11
I have seen the kernel panic message when a friend tried to install ubuntu on an old computer with insufficient ram.

---

### Post by lidewei on 2010-05-11
Thanks for your reply. I don't think that's the problem in this case though, because my computer has 4 GB ram.

---

### Post by James78 on 2010-05-11
Did you install using Wubi? If not, then boot into a livecd, and run 'sudo e2fsck /dev/sdx#', of course replacing x with the drive letter and # with the partition number, mine's sdb1. And, if you did install using Wubi, then boot into Windows, and defragment c:\ubuntu\disks\root.disk in Windows.

---

### Post by lidewei on 2010-05-11
I installed in several partitions, sda1 for /boot and sda2 for /.
I'm assuming I should use sudo e2fsck /dev/sda2 then?

---

### Post by James78 on 2010-05-11
Yup. And I'd also run it on /dev/sda1 just to be safe. If both of them report back as clean, use the -f argument to force it to check the drive regardless, sometimes the drive reports back clean when it isn't.

(Make sure the drives are unmounted first, as fixing something on mounted drives can corrupt the whole thing)

---

### Post by lidewei on 2010-05-11
Okay, the partitions both came up clean, even with -t. I tried booting Kubuntu again but I gave me another kernel panic.

---

### Post by James78 on 2010-05-11
I've noticed this trend recently. It's been happening to quite a few people recently, when it wasn't the filesystems problem. I still haven't found out the cause or the fix yet unfortunately. But here are a few tips for you:

If it's not the filesystem, it could be:
1) The kernel, try using a different version kernel (upgrading or downgrading).
2) It could be initramfs, just mkinitramfs (located in package initramfs-tools) and, if it is at all possible to mount the drive, backup the other one, and replace it, make sure the kernel version of your initramfs is the same as the kernel version.

Unfortunately, all this stuff will have to be done over a livecd. If you feel like it, it might be possible to get it to boot by editing the grub boot entry, using the e hotkey I think (it will state what key to use to edit the entries). If all else fails, I don't see what else to do except wipe the drive and reinstall and hope it works that time.

Good luck!

---

### Post by lidewei on 2010-05-11
I think the easiest way for me is to just reinstall. 
Thank you for your help. :)

---

### Post by lidewei on 2010-05-11
I reinstalled, but still the same problem...

---

### Post by James78 on 2010-05-11
Eeeek, we'll have to find a solution to this then.. I'm gonna go do a little searching.

---

### Post by lidewei on 2010-05-11
Thanks, I appreciate that!
In the meantime I booted the livecd, chrooted into the new installation and tried to do an update in the hope that it would help. The update ended with an error that said someting about initramfs (I think) and there not being enough space on the device. I did a df -h and found that my /boot is almost full, do you think the kernel panic could have something to do with that?

---

### Post by kio_http on 2010-05-11
> **lidewei said:**
> I think the easiest way for me is to just reinstall. 
Thank you for your help. :)

If this fails, please submit a bug report on launchpad.net. Chose package kernel.

---

### Post by kio_http on 2010-05-11
> **lidewei said:**
> Thanks, I appreciate that!
In the meantime I booted the livecd, chrooted into the new installation and tried to do an update in the hope that it would help. The update ended with an error that said someting about initramfs (I think) and there not being enough space on the device. I did a df -h and found that my /boot is almost full, do you think the kernel panic could have something to do with that?

What is the filesystem type for your /boot partition.

I would advise using the Kubuntu alternate Disk.
If your machine has an x86-64 CPU with 1GB + Ram go for the 64 bit alternate disk.
Else if its an x86 CPU with 512 Mb + RAM use 32 bit alternate disk.

---

### Post by lidewei on 2010-05-11
I repartitioned the disk to make a larger /boot partition, and now Kubuntu boots perfectly! 
Thanks everyone for your help. :)

---

### Post by James78 on 2010-05-11
Ahhhhh. I see. Well, good thing it's fixed now.:)

---

