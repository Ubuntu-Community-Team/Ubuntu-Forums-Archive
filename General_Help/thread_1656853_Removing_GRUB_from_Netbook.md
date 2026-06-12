---
title: "Removing GRUB from Netbook"
date: 2010-12-31
forum: General Help
---

### Post by lewis_morris on 2010-12-31
Hi

I have a acer aspire one netbook which was duel booted with the latest version of Ubuntu but as i've stopped using the netbook as much and my family use it more, i removed ubuntu for them. But i just deleted the partion and now i am stuck with the grub luncher when i boot up saying Grub Rescue, partion not found, i can only boot via USB as its a netbook!

Any help would be much appreciated.

Thanks 

Lewis

---

### Post by wilee-nilee on 2010-12-31
> **lewis_morris said:**
> Hi

I have a acer aspire one netbook which was duel booted with the latest version of Ubuntu but as i've stopped using the netbook as much and my family use it more, i removed ubuntu for them. But i just deleted the partion and now i am stuck with the grub luncher when i boot up saying Grub Rescue, partion not found, i can only boot via USB as its a netbook!

Any help would be much appreciated.

Thanks 

Lewis


It would help if you named what is left on the computer.

Do you have a cd/dvd reader you can plug in.

Do you have Ubuntu live cd on a thumb still? If you do boot it live, and run and post the output from.
```
sudo fdisk -lu
```

If you have a version of windows and that is all you want on there, there is a Linux bootloader that can be loaded from a booted Ubuntu live cd/thumb.

---

### Post by Brandon Williams on 2010-12-31
Are you able to boot into Windows, perhaps with a rescue disc of some sort? If you can, then you should search for instruction to restore the Master Boot Record (MBR) using the rescue disc.

If you can't get into Windows or boot from a Windows rescue disc, then you could try booting into a live Ubuntu distro using a USB stick for repairs. I suggest the following actions once you boot into the live distro. First, install the mbr package with 'sudo apt-get install mbr'. Then overwrite your existing mbr with 'sudo install-mbr /dev/sda'. Then attempt to reboot from the hard drive. The MBR installed in this way is very simple. By default, it will attempt to boot from the default bootable partition, which in this case should be your Windows partition.

If the above fix works, then you should return to my first suggestion. After you boot into Windows, search with Google to find instructions for reinstalling the MBR from within your version of Windows.

---

### Post by wilee-nilee on 2010-12-31
> **Brandon Williams said:**
> Are you able to boot into Windows, perhaps with a rescue disc of some sort? If you can, then you should search for instruction to restore the Master Boot Record (MBR) using the rescue disc.

If you can't get into Windows or boot from a Windows rescue disc, then you could try booting into a live Ubuntu distro using a USB stick for repairs. I suggest the following actions once you boot into the live distro. First, install the mbr package with 'sudo apt-get install mbr'. Then overwrite your existing mbr with 'sudo install-mbr /dev/sda'. Then attempt to reboot from the hard drive. The MBR installed in this way is very simple. By default, it will attempt to boot from the default bootable partition, which in this case should be your Windows partition.

If the above fix works, then you should return to my first suggestion. After you boot into Windows, search with Google to find instructions for reinstalling the MBR from within your version of Windows.

It is much more straight forward then this searching around.:)

I can help this user with loading a recovery if it is Vista or W7 to a thumb, or just using the standard Linux replacement loader Lilo.

---

