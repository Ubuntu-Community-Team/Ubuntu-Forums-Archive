---
title: "grub2 boots with grub prompt most of the time"
date: 2010-06-06
forum: General Help
---

### Post by peteym5 on 2010-06-06
I am having this issue with my grub2 boot loader that it boots into the grub prompt. This happens almost right after updating to the latest kernel 2.6.32-22 (I believe)

I copied down the instructions of what to do in this case to get into linux (set root=(hdx,x; linux /boot/vmlinuz... initrd /boot/initrd.... boot) which starts a load but eventually times out saying it cannot find root or something like that.

I also tried to repair a broken system from the kubuntu live dvd and tried to manually install grub from booted linux on the dvd. I have re-installed Kubuntu several times. I will be checking if its an issue involving the SATA cables coming loose or an HD overheating because my computer had that happen before.

I have Linux installed on my 2nd HD, first partition (HD1,1) or SDB1. with Windows 7 on the First Hard Drive, First Partition. My computer uses a AMD64 Duel Core Processor. 2GB ram. Both HDs are SATA.

You all know this is inconvenient since locks anyone out from any operating system and therefore have no access to the internet unless they have another computer. Not everyone is a grub geek and know about the Ubuntu Grub 2 Wiki when they first try to use Linux.

---

### Post by Leppie on 2010-06-06
you say you've installed kubuntu several times, does this issue only appear after the kernel is updated to version 2.6.32-22?
or does this issue occur before this as well?

---

### Post by peteym5 on 2010-06-06
it happened right after 2.6.32-22. this was included with a bunch of other updates and bug fixes so we cannot be sure if the new kernel update is causing it. I removed the latest kernel and it still happened.

---

### Post by peteym5 on 2010-06-06
I should mention the prior installations were going to HD(1,5) or SDB5. I had to go into windows and delete the partions, reboot with the Kubuntu 10.4 DVD and it installed to HD(1,1) SDB1. The partition was once used by WindowsXP up last fall. I think that invisible partition used by Windows was still there and messing up the partition table. I deleted all the partitions except for one in the middle of the HD and created some new ones before and after it. I don't think that is the origins of this problem.

My last action was to boot the Windows Disk and redo the BOOT and MBR. Was the only way I can boot into an usable OS and get online to research this problem further.

---

