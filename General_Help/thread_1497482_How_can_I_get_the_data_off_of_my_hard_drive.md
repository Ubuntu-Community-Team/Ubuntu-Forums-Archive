---
title: "How can I get the data off of my hard drive?"
date: 2010-05-30
forum: General Help
---

### Post by Vatra on 2010-05-30
I just switched computers. The new computer has only one place on the ribbon cable for hard drives. I had one hard drive with Windows on it, and another with Linux Mint on it in the old computer. I know this forum is for Ubuntu, but I figured this was the best place to ask about this, since LM is based on Ubuntu. I can't see the Linux hard drive in my computer from Windows 7 through a USB to IDE and SATA cable. How do I get the stuff from my Linux hard drive off?

---

### Post by dv3500ea on 2010-05-30
You can't get the data in Windows because Windows doesn't support the file system you have on the drive (probably ext3 or ext4). You could potentially use Linux to transfer the files to the windos drive as linux supports Windows' file system. It would probably be easier if you could copy your files to an external drive or DVD. Another thing you could try is finding an ext3/ext4 file system driver for Windows.

---

### Post by Vatra on 2010-05-30
> **dv3500ea said:**
> You can't get the data in Windows because Windows doesn't support the file system you have on the drive (probably ext3 or ext4). You could potentially use Linux to transfer the files to the windos drive as linux supports Windows' file system. It would probably be easier if you could copy your files to an external drive or DVD. Another thing you could try is finding an ext3/ext4 file system driver for Windows.

Yeah, I forgot to mention that I can't boot from the Linux hard drive. The screen just stays black. Would using a Super GRUB Disk work, as far as at least booting into the Linux hard drive? That way I could connect the Windows hard drive through the USB to IDE and SATA cable.

---

### Post by amite on 2010-05-30
what is your filesystem for linux system?if it is ext4 or any other than ext2 or ext3 then i don't know what to do!but if filesystem is ext2 or ext3 then install drivers for that filesystem it is free available.
this link may hel u:[http://www.linuxquestions.org/questions/linux-newbie-8/ext3-driver-for-windows-511913/](http://www.linuxquestions.org/questions/linux-newbie-8/ext3-driver-for-windows-511913/)

---

### Post by dv3500ea on 2010-05-30
> **Vatra said:**
>  Would using a Super GRUB Disk work, as far as at least booting into the Linux hard drive?
Possibly, or you could use a live CD to read and copy the files.

---

### Post by N8N on 2010-05-30
Just boot into Linux and then try to access the files through the USB converter.  I've had no luck trying to do this through a live CD, but a real functional Linux system should work just fine.

---

### Post by BoneKracker on 2010-05-30
Or you could just transfer the files over Ethernet.

---

### Post by Vatra on 2010-05-31
> **BoneKracker said:**
> Or you could just transfer the files over Ethernet.

How would I go about doing that?

---

### Post by BoneKracker on 2010-05-31
> **Vatra said:**
> How would I go about doing that?

Assuming both computers have an ethernet network adapter, you can do any of the following:

a) Plug both machines into the same network, and transfer the files using samba or ssh or something.

If you don't have a network you can plug both machines into, you may be in a position to easily borrow an ethernet hub, switch, or router and set up an ad-hoc network. Plug the device in to power, connect both machines to it by ethernet, then get both machines on the same network (i.e., give them both static addresses in the name subnet, such as 192.168.0.10 and 192.168.0.11).

Then transfer the files. If you're running sshd on one of the machines, then from the other, you can open Nautilus and type ssh://192.168.0.11 (or the appropriate address), then just drag the files over.  Or, you could use samba and a shared directory.

b) If you don't have a network and can't set one up or bring your computers to someone else's network temporarily, then you could get an ethernet crossover cable at Radio Shack or wherever, and just connect their ethernet adapters directly to each other, then proceed as above.

If that is beyond your capability, then you might want to just use a USB thumb drive or something.

A third possibility would be to reverse the use of your "USB to IDE and SATA cable" (plug it into the USB on the old computer and connect the new hard drive on the new computer to it, then mount the ntfs partition and move your files into it).

A fourth possibility is whether you could just stick a normal ribbon cable (with two connectors) in there and connect both drives.

---

### Post by Vatra on 2010-05-31
> **BoneKracker said:**
> Assuming both computers have an ethernet network adapter, you can do any of the following:

a) Plug both machines into the same network, and transfer the files using samba or ssh or something.

If you don't have a network you can plug both machines into, you may be in a position to easily borrow an ethernet hub, switch, or router and set up an ad-hoc network. Plug the device in to power, connect both machines to it by ethernet, then get both machines on the same network (i.e., give them both static addresses in the name subnet, such as 192.168.0.10 and 192.168.0.11).

Then transfer the files. If you're running sshd on one of the machines, then from the other, you can open Nautilus and type ssh://192.168.0.11 (or the appropriate address), then just drag the files over.  Or, you could use samba and a shared directory.

b) If you don't have a network and can't set one up or bring your computers to someone else's network temporarily, then you could get an ethernet crossover cable at Radio Shack or wherever, and just connect their ethernet adapters directly to each other, then proceed as above.

If that is beyond your capability, then you might want to just use a USB thumb drive or something.

A third possibility would be to reverse the use of your "USB to IDE and SATA cable" (plug it into the USB on the old computer and connect the new hard drive on the new computer to it, then mount the ntfs partition and move your files into it).

A fourth possibility is whether you could just stick a normal ribbon cable (with two connectors) in there and connect both drives.

You, sir, are a genius. Thank you. I think replacing the ribbon cable would work the best, because I can't seem to boot from the Linux hard drive without having the Windows hard drive in the same computer.

---

### Post by BoneKracker on 2010-05-31
> **Vatra said:**
> You, sir, are a genius. Thank you. I think replacing the ribbon cable would work the best, because I can't seem to boot from the Linux hard drive without having the Windows hard drive in the same computer.

If your old computer was like this:

Drive 0 (Master): Windows
Drive 1 (Slave): Linux

Then you probably installed GRUB's stage 1 bootloader onto the MBR of the Windows drive.  That would be why you can't boot linux now without the Windows drive being present in the same machine.

You can resolve that by booting into Linux and reinstalling GRUB onto the MBR of the Linux drive itself.  (That's what I usually advise people to do anyway, to avoid over-writing the Windows bootloader on the MBR of the Windows drive).

Then, you just tell your BIOS that Drive 1 (not Drive 0) is the "boot disk", and when you boot, it will load GRUB.  And, if you decide to yank Linux from the computer, you just switch the BIOS back to booting from Disk 0, and its like Linux was never there (the Windows bootloader is untouched).

So, if you want to move your Linux drive over to your new computer: you could get on your old computer, boot into Linux, install GRUB onto the MBR of the Linux drive.  Put a two-connector ribbon cable in the new computer, put the Linux drive in the slave position in the new computer, boot into the BIOS setup on the new computer, tell the BIOS to boot from the Linux drive, and then reboot.  GRUB should show up after you boot, and you can boot into Linux.

However, your old "Windows" entry might not work any more (because it was set up for XP).  I really don't know anything about that, as I haven't done a dual-boot for years.  To fix that, you'd probably then have to reinstall GRUB again, or otherwise reconfigure GRUB to make the Windows menu entry work properly for Windows 7.  Once you get Linux booting, you could ask again for help on that from an Ubuntu dual-boot user.

Good luck.

---

### Post by Vatra on 2010-05-31
> **BoneKracker said:**
> If your old computer was like this:

Drive 0 (Master): Windows
Drive 1 (Slave): Linux

Then you probably installed GRUB's stage 1 bootloader onto the MBR of the Windows drive.  That would be why you can't boot linux now without the Windows drive being present in the same machine.

You can resolve that by booting into Linux and reinstalling GRUB onto the MBR of the Linux drive itself.  (That's what I usually advise people to do anyway, to avoid over-writing the Windows bootloader on the MBR of the Windows drive).

Then, you just tell your BIOS that Drive 1 (not Drive 0) is the "boot disk", and when you boot, it will load GRUB.  And, if you decide to yank Linux from the computer, you just switch the BIOS back to booting from Disk 0, and its like Linux was never there (the Windows bootloader is untouched).

So, if you want to move your Linux drive over to your new computer: you could get on your old computer, boot into Linux, install GRUB onto the MBR of the Linux drive.  Put a two-connector ribbon cable in the new computer, put the Linux drive in the slave position in the new computer, boot into the BIOS setup on the new computer, tell the BIOS to boot from the Linux drive, and then reboot.  GRUB should show up after you boot, and you can boot into Linux.

However, your old "Windows" entry might not work any more (because it was set up for XP).  I really don't know anything about that, as I haven't done a dual-boot for years.  To fix that, you'd probably then have to reinstall GRUB again, or otherwise reconfigure GRUB to make the Windows menu entry work properly for Windows 7.  Once you get Linux booting, you could ask again for help on that from an Ubuntu dual-boot user.

Good luck.

Thanks a lot. I think I have everything I need, now. :)

---

