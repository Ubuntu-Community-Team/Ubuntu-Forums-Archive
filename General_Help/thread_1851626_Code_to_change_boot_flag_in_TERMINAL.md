---
title: "Code to change boot flag in TERMINAL"
date: 2011-09-28
forum: General Help
---

### Post by fnyahoo on 2011-09-28
Good Day:

What is the code to change the boot flag from sdb1 to sdb2 in Terminal (not using Gparted)? Thanks in advance for your help!

---

### Post by papibe on 2011-09-28
Welcome to the forums!

Could you explain a little bit more what you want to do?

My first guess is that you bought a new hard drive and want to use it as primary disk. Is that it?

Regards.

---

### Post by oldfred on 2011-09-28
Grub does not use boot flag, Windows does and you need it on the Windows partition if you ever have to do repairs.

set boot flag on for sdb2 (off on others)

```
sudo sfdisk -A2 /dev/sdb
```

Some bios refuse to boot a hard drive without a boot flag. Although grub does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.
Many Intel BIOSes, though, have a bug that requires that at least one MBR partition be marked as bootable, so you'll need to use fdisk (not gdisk, parted, or GParted) to mark the 0xEE partition as bootable/active. Note this is an Intel-specific bug;

---

### Post by fnyahoo on 2011-09-28
I found the answer in a different forum. What i was looking for was "parted /dev/sdb set 2 boot on"

What i m trying to do is actually is very interesting and can help others if they r interested. I want to have Ubuntu Prsistent Live and Backtract Live(not Persistent) on the same usb drive. 

I have tried so many ways but it wouldnt work. But today here is the solution that i came up with and it seems like it is working. What i did was i format the usb drive into two partitions fat32. By using UNetBootin  i installed ubuntu in one partition and backtrack in the other one. But i couldnt choose which os to start at unetbootin start up. Since i installed backtrack after ubuntu, unetbootin would start backtrack at start up. In the usb there is ununtu and backtrack but i had to change the boot flag in order to change unetbootin's start up os. Backtrack doesnt have gparted. Thats why i needed to figure out how to change the boot flag throught the terminal. Now what i do is i log into lets say ubuntu lets say in sdb1 through unetbootin on the usb then if i want to change the os to backtrack i change the boot flag to sdb2 in ubuntu before restart then when i restart and i chose to boot from usb, unetbootin logs in and opens the backtrack options. Then i login to backtrack. If i wantt o change to ubuntu then in backtrack i change the boot flag in terminal again to ubuntu then reboot start from usb unetbootin loads ubuntu :))) 

I had written here before thats what i wanted  to do so it seems like i found the solution. It would be much better if i could work in grub meaning that i start the computer from the usb and at grub choose either ubuntu persistent or backtrack live. That would be the best but i couldnt do it that way. If you have a better way of doing it let me know. But for now thats what i ll be suggesting people. 

The main reason why i wanted to have the ubuntu persistent is because i dont want to change the settings everytime and install necessary packages everytime. But in Bactrack i dont want to mess up the settings so i want a clean default backtrack everytime i log in. Thats why. Makes sense?

---

### Post by oldfred on 2011-09-28
You should be able to use grub2. But have to manually create the grub.cfg file with the correct boot stanza.

I use grub2 to boot multiple ISO and have it booting a Windows repairUSB with grub in the windows repair partition. It also boots other ISOs in another partition.

With grub2 persistent C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistent 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive or different partition.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by fnyahoo on 2011-09-28
Ok i was too early to celebrate! I had a problem on the persistent ubuntu. After following unetbootin's way of doing ubuntu persistent (copying the casper. file from their website and editing syslinux file) is not working properly for a persistent os. It gives errors with the root and i changed the settings in firefox for example and i reboot the ubuntu and the firefox wouldnt start anymore. So there are problems with unetbootin's persistent way. I have to find a perfect way of doing ubuntu persistent. Changing the boot flag is a good option to have.

---

