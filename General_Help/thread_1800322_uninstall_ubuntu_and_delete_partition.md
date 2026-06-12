---
title: "uninstall ubuntu and delete partition"
date: 2011-07-08
forum: General Help
---

### Post by arctic_tux on 2011-07-08
hi,

i have installed Ubuntu on a 1tb external hdd and am wanting to uninstall Ubuntu as i don't need it anymore (i have a dual boot win xp). My computer will not run any OS at all if the external drive is not connected (xp is on an internal drive). I need to free up the drive so i can use it on another computer.

the non Ubuntu partition is in the NTFS format
the external HDD is connected by a USB port
the bios says it is the secondary master HDD
i am running Ubuntu 11.04 and Win XP (SP2)
i am not a complete novice at this type of thing but i am no expert.
or would it be easier to take it into a computer shop and get them to do it

Any ideas 

It is not urgent

thanks

---

### Post by JC Cheloven on 2011-07-08
If I understand correctly, you have xp + ubuntu in your internal disk, and yet another ubuntu install in your external 1Tb usb disk. 

The boot files (grub) are probably in the external disk, this being the reason why the pc can't boot without it plugged in.

If the above is true, just fire up with the usb disk plugged in, but boot in the ubuntu which is at your internal disk. Once there run 
```
sudo grub-install --recheck /dev/sdx

```
Where sdx is the internal disk, probably sda (but check first, twice!, with sudo fdisk -l) 


Shutdown, and fire up again without your external disk. You should be able to boot from your internal disk.

---

### Post by lmarmisa on 2011-07-08
If you wish to restore the XP MBR loader in your internal hard drive, boot into Ubuntu, open a terminal and type this command:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```

If you restore the XP loader, you will be only able to boot into XP. Once you have upgraded the MBR loader, you will be free to get rid of the Ubuntu partitions located in your internal hard drive.

Best regards,

Luis

---

