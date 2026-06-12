---
title: "Kubuntu 11.04 Grub2 Dual Boot Problem"
date: 2011-08-22
forum: General Help
---

### Post by MattBarszcz on 2011-08-22
Hello,
  I have dual booted ubuntu many times before with Windows 7 and it has worked without issue, but this time I am struggling to get Windows to boot.   I have Kubuntu 11.04 installed alongside Windows 7.  The partitions on the drive are laid out as follows:

sda1 Windows System Reserved (300M)
sda2 Windows 7
sda3 SWAP
sda4 (LVM)
 -sda5 /boot
 -sda6 /

In retrospect I suppose I should have put the SWAP and / inside the LVM and /boot as a primary partition, but if I can work with what I have that would be best.

I ran a 

```
sudo grub-probe -t device /boot/grub
```and it confirms that grub2 is installed on sda5.

Now for the problem...
grub2 is setup to load windows 7, and there is an entry in the list for Windows 7 (loader on /dev/sda1).  The installer created this automatically.  When I choose this option in the bootloader though, the screen blinks black (as if it is chainloading windows) and then the grub menu comes back up (no errors though).  It seems as if the Windows chainloader entry is somehow pointing back at grub itself.

I know I could get it to work if I reinstalled the Windows bootloader, changed around the linux partitions, and reinstalled kubuntu (this time with the bootloader on the mbr), but I would like to be able to salvage this install of kubuntu if possible.

Any help is greatly appreciated.

Thanks,
Matt

---

### Post by MattBarszcz on 2011-08-23
bump

---

