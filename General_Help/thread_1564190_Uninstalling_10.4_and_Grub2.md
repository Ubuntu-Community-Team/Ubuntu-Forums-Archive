---
title: "Uninstalling 10.4 and Grub2"
date: 2010-08-30
forum: General Help
---

### Post by clevedale on 2010-08-30
I installed Ubuntu 10.4 (32 bit) version on a Dell Inspirion 6000 Lap top ( I don't think it matters since I have a new hard drive and no Dell software)
I installed it "side by side" and kept my Windows XP Home Version. 

I want to uninstall Ubuntu for now. I don't know how to do it? I deleted the partitions but then I get a boot error because it looks like it is still using Grub2 for booting even after the two partitions have been removed. 

I do not have the Windows XP CD but I do have my license number on the bottom of my computer. I really don't want to wipe my hard drive anyway. I want to uninstall Ubuntu for now and try Linux Mint. 

Forgive me if this info is somewhere else, if it was I wasn't able to find it.
I am new at this so help in laymen terms would be great.

Thanks in advance.:)

---

### Post by TNT1 on 2010-08-30
> **clevedale said:**
>  I deleted the partitions but then I get a boot error because it looks like it is still using Grub2 for booting even after the two partitions have been removed. 

I do not have the Windows XP CD but I do have my license number on the bottom of my computer. I really don't want to wipe my hard drive anyway. I want to uninstall Ubuntu for now and try Linux Mint. 

.

That's cause grub resides outside of the partition. You should be able to boot from a mint live cd, it will recognise the partitions, and you can install it the same way you did ubuntu. 

Does grub still list XP when you boot?

---

### Post by lmarmisa on 2010-08-30
Try to follow my procedure for fixing the MBR of your hard drive:

[http://ubuntuforums.org/showthread.php?t=1564188](http://ubuntuforums.org/showthread.php?t=1564188)

---

### Post by clevedale on 2010-08-30
> **TNT1 said:**
> That's cause grub resides outside of the partition. You should be able to boot from a mint live cd, it will recognise the partitions, and you can install it the same way you did ubuntu. 

Does grub still list XP when you boot? No it doesn't, there is an error with only a command prompt.

---

### Post by clevedale on 2010-08-30
> **lmarmisa said:**
> Try to follow my procedure for fixing the MBR of your hard drive:

[http://ubuntuforums.org/showthread.php?t=1564188](http://ubuntuforums.org/showthread.php?t=1564188)

Thanks for the link but I don't understand what they are talking about or how it relates to my situation?

I just want to uninstall Ubuntu and return my computer to Windows only. Then I would like to install Mint inside of windows.
Thanks

---

### Post by sarin_cv on 2010-08-30
you don't have to uninstall ubuntu to install linuxmint. You can run linuxMint installtion cd and just point to the partition on which u installed ubuntu. On installtion, it will correct the boot record and you can boot in to windows.

---

### Post by clevedale on 2010-08-30
> **TNT1 said:**
> That's cause grub resides outside of the partition.


Is there a way to find the grub and delete it?

---

### Post by lmarmisa on 2010-08-30
Follow my procedure, clevedale. This is what you are looking for.

---

### Post by sarin_cv on 2010-08-30
> **clevedale said:**
> Is there a way to find the grub and delete it?

that's what lmarmisa was trying to say I guess...

---

### Post by TNT1 on 2010-08-30
> **clevedale said:**
> Thanks for the link but I don't understand what they are talking about or how it relates to my situation?

I just want to uninstall Ubuntu and return my computer to Windows only. Then I would like to install Mint inside of windows.
Thanks

As per the link, boot with an Ubuntu or Mint (or any live distro) cd, open a terminal and type: sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda, when you reboot, take the cd out, and windows will boot. Clean and resize the partitions inside windows then.

---

### Post by lmarmisa on 2010-08-30
This is another reference to a similar problem:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9207098](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9207098)

---

### Post by clevedale on 2010-08-30
> **lmarmisa said:**
> Try to follow my procedure for fixing the MBR of your hard drive:

[http://ubuntuforums.org/showthread.php?t=1564188](http://ubuntuforums.org/showthread.php?t=1564188)

Hey that worked like a charm. I am re-posting your solution from the link so someone doesn't have to click around so much. 

[I]lmarmisa's Solution "I recommend you to repair the loader of the Master Boot Record of your  hard drive. After that, you will be able to run your XP system.

Start your system from an Ubuntu Live CD (you may have to hit F12 during reboot and highlight boot from CD), open terminal (found in applications) and type this command (yes leave the spaces where indicated):[/I]  [I]      Quote:
                                                 sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda                                 
Then reboot the system extracting the Live CD. Windows XP will start normally.[/I]

After doing this I went to disk management and deleted the two extra partitions. I am installing mint inside of windows to give it a try. Thanks to all that replied and a real BIG THANKS again to lmarmisa

---

### Post by lmarmisa on 2010-08-30
A last comment: this solution is valid only for restoring the MBR loader of Windows XP. Do not try it for Vista or Windows 7.

---

### Post by Blook on 2010-08-30
I don't know whether an uninstaller help you or not. For my problem, when having uninstall problems, I always return to an uninstaller. Maybe[ this]("http://www.pchelpdiy.com") will help you!

---

