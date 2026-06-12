---
title: "Installed ubuntu, but i want to delete windows"
date: 2010-05-25
forum: General Help
---

### Post by fullexplorer on 2010-05-25
Hello people, some days ago i installed Ubuntu 10.4 but i have a problem, i want to delete windows and only have ubuntu in my PC, but i dont know where can i delete it!

Please a tutorial to have only Ubuntu in my PC?

Thanks for reading, i`ll wait the help

---

### Post by SlidingHorn on 2010-05-25
A quick earch of the forums found several threads telling how to do this...like this one: [http://ubuntuforums.org/showthread.php?t=485514](http://ubuntuforums.org/showthread.php?t=485514)

---

### Post by perspectoff on 2010-05-25
> **fullexplorer said:**
> Hello people, some days ago i installed Ubuntu 10.4 but i have a problem, i want to delete windows and only have ubuntu in my PC, but i dont know where can i delete it!

Please a tutorial to have only Ubuntu in my PC?

Thanks for reading, i`ll wait the help

I'll make these assumptions:

1) You've been using your Ubuntu/Kubuntu OS for some time and re-installation is not an option (since this would be the easiest method).

2) You have a relatively small hard drive and you want to reclaim some space that the Windows OS is hogging up.

3) You have only two operating systems (Windows and (K)Ubuntu) and the GRUB installer has the (K)Ubuntu OS listed first (which is what usually happens in routine (K)Ubuntu installations).

In this case, obtain and burn the GParted LiveCD.

Boot into it.

Re-format the Windows NTFS partition as ext3 (or anything you want, even leaving it at NTFS). This will wipe it clean. Shrink the (formerly) Windows partition to 100 Mb (or something similarly small). This preserves the partition numbering system and only wastes a mere 100 Mb.

Grow the (K)Ubuntu partition until it fills the new free space that was left behind by shrinking the Windows partition.

Restart your computer.

The benefit of leaving a (small) partition in place as a "placeholder" on the hard drive is that if you ever change your mind, it will be able to reverse the steps just described fairly easily. Also, with this method you won't need to fiddle with the Grub bootloader.

---

### Post by MC_Sketch on 2010-05-25
im not sure if it's in 10.04 because im updating as im typing this, but in 9.10 and previous distros there's an application called "GParted" when you boot from the Live CD that you can use to edit partitions. if you have the Lucid CD or 9.10 or before, boot from the CD and delete the NTFS Windows file on the Hard Disk and you're set :)

---

### Post by fullexplorer on 2010-05-25
Ok ty, but i have a question, after desintalling Windows, how can i put the free space of the disk to ubuntu? or something like that...

Srry for my english i speak spanish.

Edit: my other problem, is that my pc dont boot the LiveCD i dont know why, and i had to install it from windows... :S

---

### Post by perspectoff on 2010-05-25
> **MC_Sketch said:**
> im not sure if it's in 10.04 because im updating as im typing this, but in 9.10 and previous distros there's an application called "GParted" when you boot from the Live CD that you can use to edit partitions. if you have the Lucid CD or 9.10 or before, boot from the CD and delete the NTFS Windows file on the Hard Disk and you're set :)

The problem with merely deleting the partition is that the partition numbering scheme then changes, and you don't know if this user has the old Grub bootloader configuration files (perhaps he/she did serial upgrades from Jaunty) which often loaded the OS based on its partition number, or GRUB2, which uses UUIDs instead (one of the few things I like about GRUB2).

(Also, I'm not actually suggesting the person is a he/she).

---

### Post by Serpher on 2010-05-25
Perspectoff: No offense but there was a lot wrong with what you said.
Easiest way to do this is open up gparted in System --> Administration --> Gparted (Or something like Disc Management depending on your version of Ubuntu). Using the GUI just delete the Windows partition and extend your Ubuntu partition.


> **perspectoff said:**
> In this case, obtain and burn the GParted LiveCD.

Boot into it.

You don't have to do this using a live CD


> **perspectoff said:**
> Re-format the Windows NTFS partition as ext3 (or anything you want, even leaving it at NTFS). This will wipe it clean. Shrink the (formerly) Windows partition to 100 Mb (or something similarly small). This preserves the partition numbering system and only wastes a mere 100 Mb.

If something was /dev/sda2 prior to the deletion, it will remain /dev/sda2 and not turn into /dev/sda1. If you use the fdisk partitioner, you will even find out you can simply just assign the number 1-4 to a primary partition.


> **perspectoff said:**
> The benefit of leaving a (small) partition in place as a "placeholder" on the hard drive is that if you ever change your mind, it will be able to reverse the steps just described fairly easily. Also, with this method you won't need to fiddle with the Grub bootloader.

You don't need to declare any free space on the hardrive to reverse the steps. When it's done it's done. If you want to reverse the changes you simply have to shrink the partition Ubuntu is using, and then install Windows in an NTFS partition you would make using the Windows CD.

Also I think it would make it a lot easier on you if you just refered to all Ubuntu distros as Ubuntu. Kubuntu is Ubuntu, but it's just packaged with different programs and desktop enviroment but is still the same OS. There's also Xubuntu, Lubuntu, Fluxbuntu, and probably more.

---

### Post by fullexplorer on 2010-05-25
> **Serpher said:**
> Perspectoff: No offense but there was a lot wrong with what you said.
Easiest way to do this is open up gparted in System --> Administration --> Gparted (Or something like Disc Management depending on your version of Ubuntu). Using the GUI just delete the Windows partition and extend your Ubuntu partition.

Yes, i saw the application "Disc Managament" but im scared about doing something wrong and crush my PC, can you give me a Tutorial how to exactly do it? Please.
My version of ubuntu is Ubuntu 10.4

---

### Post by perspectoff on 2010-05-25
> **fullexplorer said:**
> Ok ty, but i have a question, after desintalling Windows, how can i put the free space of the disk to ubuntu? or something like that...

Srry for my english i speak spanish.

Edit: my other problem, is that my pc dont boot the LiveCD i dont know why, and i had to install it from windows... :S

Si, merely resize the Ubuntu partition so that it is larger. (When you shrink the Windows partition, free space will be left behind.)

It will be obvious when you are running GParted.

You can't resize the Ubuntu partition while Ubuntu is running: that's why you need the LiveCD.

When your computer starts up, you will see a screen that says to hit ESC or DEL or F1 or F2 or F10 or something to change the BIOS settings (or boot device). You will need to do that in the first few seconds.

If you can directly select the CD to boot, do so. Otherwise enter the BIOS settings and look for the Bootup device priority. Change it so that the CD-ROM is at the top. Then save and reboot. Now you should boot from the CD.

---

### Post by perspectoff on 2010-05-25
> **Serpher said:**
> Perspectoff: No offense but there was a lot wrong with what you said.
Easiest way to do this is open up gparted in System --> Administration --> Gparted (Or something like Disc Management depending on your version of Ubuntu). Using the GUI just delete the Windows partition and extend your Ubuntu partition.


Nonsense. You can't change the partition of a running OS. It is locked.

For more complex partition problems, see my complete tutorials on installing multiple OS:

[http://kubuntuguide.org/Lucid#Installing_multiple_OS_on_a_single_computer](http://kubuntuguide.org/Lucid#Installing_multiple_OS_on_a_single_computer)

and 

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_multiple_OS_on_a_single_computer](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_multiple_OS_on_a_single_computer)

---

### Post by fullexplorer on 2010-05-25
> **perspectoff said:**
> Si, merely resize the Ubuntu partition so that it is larger. (When you shrink the Windows partition, free space will be left behind.)

It will be obvious when you are running GParted.

You can't resize the Ubuntu partition while Ubuntu is running: that's why you need the LiveCD.

When your computer starts up, you will see a screen that says to hit ESC or DEL or F1 or F2 or F10 or something to change the BIOS settings (or boot device). You will need to do that in the first few seconds.

If you can directly select the CD to boot, do so. Otherwise enter the BIOS settings and look for the Bootup device priority. Change it so that the CD-ROM is at the top. Then save and reboot. Now you should boot from the CD.

Oh ty, i think i had a problem in the protity of bootup on the bios, ill try to do something, thanks, then ill tell you...

---

### Post by Serpher on 2010-05-25
Your right about that sorry, for some reason I was thinking about LVMs with regards to resizing.

Anyway as long as you don't delete your Ubuntu partition, you're good. Just delete your Windows partition (NTFS), and on a Live CD select your Ubuntu partition, and extend it.

---

