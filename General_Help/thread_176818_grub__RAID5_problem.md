---
title: "grub / RAID5 problem"
date: 2006-05-15
forum: General Help
---

### Post by soton on 2006-05-15
Forum,

I am trying to add an NTFS RAID5 array to an existing dual boot WinXP / Ubuntu 5.10 setup, but I'm running into trouble...

XP is installed on an IDE disk (hda, hd0). Ubuntu is installed on a SATA disk (sda, hd1), connected to the SATA controller in the Nvidia chipset of my Asus K8N4-E Deluxe mobo. The 3 300Gb SATA drives that will make up the RAID array are connected to the Silicon Image SIL3114 SATA controller. 

When I boot the system, grub hangs with following message:

GRUB Loading Stage 1.5
GRUB Loading, Please Wait..
Error 5

Suspecting that sda might get renamed somehow when connecting the 3 drives, I booted the system with a Knoppix Live CD and indeed, the 3 new drives were named sda, sdb and sdc while sda had been renamed to sdd. No surprise that grub bombed out.

So I decided to try and reconfigure grub so that it was pointing to the correct partition (sdd3 instead of sda3). I created a bootable grub CD using the stage2_eltorito file and booted the system. 

At the grub> prompt, I did "find /boot/grub/stage1".

Great was my surprise when it came back with (hd1,2) where I was expecting (hd4,2). 

Could anyone please shed some light on this ? I'm a bit stuck at the moment.

Thanks,
Ivan

---

### Post by soton on 2006-05-15
I decided to reinstall Ubuntu, hoping it would sort out the problem. And so I did..

Funnily enough, in the partitioner of the installer, my old sda now had remained sda and the 3 new RAID disks were called sdb, sdc and sdd.. Ubuntu seemed to install fine until the first reboot.. grub Error 5 again :-(

I disabled the Silicon Image controller and it booted up fine.

Any ideas anyone ?

---

### Post by onlyoneskwalla on 2006-05-25
Not sure if you need to be able to boot from your Raid5 setup, but have you checked in you bios what your hard drive boot order is?  I have a similar setup with a dfi motherboard and it might set to boot the raid drives unless I set it to target the non-raid drive first.  

Also if you have no have no need to boot the raid5 config, but just need access to them from an operating system you might want to disable their bootable flag in the sil bios screen if you can.  This might solve your problem. 

Well Good Luck;)

---

