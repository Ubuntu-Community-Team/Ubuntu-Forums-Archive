---
title: "Formating partition with 7 affects ubuntu in any way?"
date: 2010-10-23
forum: General Help
---

### Post by Pavlidis on 2010-10-23
Hello, i am a newbie to the world of Linux. I recently installed to my Acer 5920G laptop, Ubuntu 10.04, alongside with Windows 7. In order to install Ubuntu i divided my hard disc into 4 partitions: 1. sda1 contains Windows 7 (ntfs), 2. sda2 contains data, 3. sda3 contains Ubuntu (ext4), 4. contains swap.

I want to format sda1 and reinstall windows 7. Is this gonna affect Ubuntu in any way? If yes what should i?

Thanks in advance for you answers

---

### Post by coffeecat on 2010-10-23
> **Pavlidis said:**
> I want to format sda1 and reinstall windows 7. Is this gonna affect Ubuntu in any way? If yes what should i?

It shouldn't affect Ubuntu itself - so long as the Windows installer restricts its attentions to sda1. But it will install the Windows MBR which will overwrite grub stage 1 in the mbr and mean that, at first, you will only be able to boot into Windows. This is easily fixed, though. You simply need the Ubuntu live CD and this link:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Just post back if you need help with it.

Out of interest - Acer laptops with W7 usually come with sda1 = recovery partition, sda2 = small boot partition and sda3 = W7 C: partition. How come you  have Windows 7 on only sda1?

---

### Post by srs5694 on 2010-10-23
There's one other possible effect: The filesystem's ID number will probably change. If you've got an /etc/fstab entry to mount the partition in Linux, and if that entry uses a UUID code to identify the filesystem rather than a device name, you'll probably have to adjust that value. This won't be an issue if you let the GNOME automounter mount the partition or if you don't need to access it from Linux.

---

### Post by Pavlidis on 2010-10-23
Originally my laptop had Windows Vista. I mounted Ubuntu's live cd and used gparted to delete all partitions. Then i created the 4 partitions i mentioned above, and installed 7 at first, and ubuntu later. By the way, gparted is the best tool of its kind, i have ever used.

---

