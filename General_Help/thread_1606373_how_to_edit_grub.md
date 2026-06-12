---
title: "how to edit grub?"
date: 2010-10-26
forum: General Help
---

### Post by sohlinux on 2010-10-26
Hi, 

When I boot my pc I get several boot options from old unused operating systems like windows 7 and ubuntu 10.04?

I am now only using ubuntu 10.10 how can I remove the unused options from grub?

Thanks
Tom

---

### Post by Quackers on 2010-10-26
Plenty to get you going in this thread

[http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+menu+items](http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+menu+items)

---

### Post by sohlinux on 2010-10-26
> **Quackers said:**
> Plenty to get you going in this thread

[http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+menu+items](http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+menu+items)

thanks for the link, I followed that carefully and removed the old ubuntu but still I have the following 2 entries

Windows Vista (loader) (on /dev/sda1)

Windows 7 (loader) (on /dev/sda2)

any ideas how to get rid of those? is there some sort of gui for edit grub? startup-manager gui only lets me change the default not remove.

Tom

---

### Post by Quackers on 2010-10-26
Is Windows still a bootable OS?

---

### Post by sohlinux on 2010-10-26
> **Quackers said:**
> Is Windows still a bootable OS?

I have 6 partitions on this pc. windows is not bootable now I have deleted all the files but it looks like the loaders are still in there somewhere.

 
this is a sony vaio it has the following

windows 7 ntfs recovery partition on /dev/sda1

windows 7 ntfs filesys on /dev/sda2

ubuntu 10.10 on /dev/sda3

ubuntu 10.04 on /dev/sda7 (files have been deleted)

ubuntu 10.10 swap on /dev/sda6

ntfs free space on /dev/sda5 (windows 7 was installed here- files have been deleted)

I want to keep Windows Vista (loader) (on /dev/sda1) in case I want to restore windows 7

can I safely delete Windows 7 (loader) partition (on /dev/sda2)???

Tom












 
Tom

---

### Post by Quackers on 2010-10-26
In a terminal run
sudo update-grub
and watch to see if the Windows loaders are picked up while grub.cfg is configured.
If they are, and you have no need of Windows in the future, you can delete the Windows partitions (with Gparted or the GParted Live CD) then run 
sudo update-grub
again and they will disappear.

---

### Post by sohlinux on 2010-10-26
> **Quackers said:**
> In a terminal run
sudo update-grub
and watch to see if the Windows loaders are picked up while grub.cfg is configured.
If they are, and you have no need of Windows in the future, you can delete the Windows partitions (with Gparted or the GParted Live CD) then run 
sudo update-grub
again and they will disappear.

Thanks, sounds like a great plan

I want to keep Windows Vista (loader) (on /dev/sda1) in case I want to restore windows 7

but can I safely delete Windows 7 (loader) partition (on /dev/sda2)??? this is a 105MB partition with windows boot folder and bootmgr file. the /dev/sda1 10GB partition is all I need to restore windows?

Tom

---

### Post by stinkeye on 2010-10-26
If you want a gui, try this.
[**_[COLOR="DarkRed"]Grub Customizer[/COLOR]_**]("http://www.webupd8.org/2010/10/grub-customizer-15-released-with-grub-2.html")

---

### Post by Quackers on 2010-10-26
I believe the 105MB partition is a Windows 7 boot partition, which will be ok to delete.
First make sure that the Windows entry for /dev/sda1 does in fact boot to the recovery environment!
Alternatively, if you have made the recovery discs, as prompted by Windows when first used, you can delete all Windows partitions, as the recovery discs will reproduce them, when run.

---

### Post by sohlinux on 2010-10-26
> **Quackers said:**
> I believe the 105MB partition is a Windows 7 boot partition, which will be ok to delete.
First make sure that the Windows entry for /dev/sda1 does in fact boot to the recovery environment!
Alternatively, if you have made the recovery discs, as prompted by Windows when first used, you can delete all Windows partitions, as the recovery discs will reproduce them, when run.

Thanks for all the help, I deleted /dev/sda2 and I can still boot to the w7 recovery if I ever go back to windows so I am happy now. :P

---

### Post by Quackers on 2010-10-26
That sounds like a good compromise to me :-)

---

### Post by sohlinux on 2010-10-26
> **stinkeye said:**
> If you want a gui, try this.
[**_[COLOR="DarkRed"]Grub Customizer[/COLOR]_**]("http://www.webupd8.org/2010/10/grub-customizer-15-released-with-grub-2.html")

thanks, nice app :)

---

### Post by sohlinux on 2010-10-26
since I deleted the windows 7 boot partition and the old ubuntu 10.04 partition I now get the following error when I try to create a new partition using the free space

I am using the disk utility which comes pre packed with ubuntu 10.10

Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=135898108416
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 10017046528, type 0x27)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 10122952704, size 125771478528, type 0x83)
new part entry
looking at part 3 (offset 135895448576, size 364211340288, type 0x0f)
Entering MS-DOS extended parser (offset=135895448576, size=364211340288)
readfrom = 135895448576
MSDOS_MAGIC found
readfrom = 135898076160
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
Exiting MS-DOS parser
MSDOS partition table detected
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed


-
now I have the following partions

Windows 7 ntfs recovery partition 10GB on /dev/sda1 ok

ubuntu 10.10 126GB on /dev/sda3 ok

ntfs 250GB /dev/sda5 ok

unknown 115GB on /dev/sda6 (this is the partition which I cannot do anything with now as per error above)

the swap partition has now gone, it was on previously on /dev/sda6


I tried gparted - it says the whole hard drive is unalocated

ubuntu still boots up ok but I cannot use the 115GB free space :( 

Is there a way of fixing this?

---

