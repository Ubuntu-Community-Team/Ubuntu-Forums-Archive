---
title: "Multibooting with Grub and /boot"
date: 2006-04-08
forum: General Help
---

### Post by egghead3 on 2006-04-08
I am trying to get a multibooting system setup with windows, ubuntu32 and ubuntu64. For the past few months, I have run a system with only ubuntu32 present. I want to have a partition setup somewhat like the following:

windows - 20gigs
ubuntu32 - 20gigs
ubuntu64 - 20gigs
large shared data partition
shared swap

I have been able to successfully get everything working simply by manually using the partition manager during installation and allowing each ubuntu installation to install grub. My problem is this. I installed ubuntu32 first, and later ubuntu64. When I went to update the kernel in my ubuntu32 to K7, the new kernel image did not appear in grub. This is because the menu.lst file that was updated by apt was that in the /boot folder on my ubuntu32 partition, whereas the menu.lst folder in my /boot folder on my ubuntu64 partition was the active menu.

I am unsure of the best way to resolve this problem. I am not really familiar with editing grubs menu.lst file manually to add new kernel images or distro installations. It would also be nice to have the grub menu automatically updated when I install a new kernel image via apt in either ubuntu32 or ubuntu64, as it did when only one of the distros was present.

One idea I had was to make a /boot partition of a 100mb or so and share it between two distros, but as someone who is fairly new to linux I really have no idea if that is acceptable, especially since the /boot partition would hold kernel images that are not necessarily compatable with the distro I would want to run at any given time.

For those of you who multiboot, what do you do? Did you simply learn how to manage grub manually? Am I missing something easy or obvious?

---

### Post by ksudbury on 2006-04-08
Yes you can make a boot partition and share it between distros, thats fine. If it was me thats what I would of done, create a 125mb / 256mb /boot make sure the boot flag is on for that partition and then edit the grub.conf if I needed to after it has updated each kernel. 

If you need help setting up grub etc post back and I will explain. Please do use google first to findout / read as much as you can. 

Let me know how you get on

Keith

---

### Post by lha on 2006-04-10
I prefer installing multiple instances of grub if possible. If your Ubuntu32 is installed on a primary partition, you can install grub to the boot sector of that partition and use your current grub (from mbr) to chainload the grub on Ubuntu32's partition. Both grub's will have their own configuration files, so when you install a new kernel to either one, it will be automatically accessible to you.

---

