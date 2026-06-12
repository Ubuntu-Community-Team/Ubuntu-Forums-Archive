---
title: "Help! I installed ubuntu loader on the same partition as windows"
date: 2012-01-15
forum: General Help
---

### Post by tofoko on 2012-01-15
Now i can't load windows 7. When i try it just start the loader menu. I am able to start windows with a recovery CD, but it is far from optimal.

I tried boot-repair, but it tells me that it detects a raid setup, but i am not.. From there nothing happens, so seems like i can,t use that application.

Maybe there is a workaround ?

---

### Post by oldfred on 2012-01-15
Welcome to the forums.

From boot repair post the bootinfoscript link it creates. Use the test version of script as it has some improvements and seems to work without any issues.

If hard drive was ever in a RAID set or if youever  turned RAID on in BIOS, it writes meta-data to drive that causes problems. But some vendors ship systems with RAID auto set up. May be best to see the output from boot info script first:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by tofoko on 2012-01-15
Tank you very much!

Here is the info:
[http://paste.ubuntu.com/805623/](http://paste.ubuntu.com/805623/)

It is notebook (asus a53ta) with only one hdd and i have not tried to make it raid.

---

### Post by oldfred on 2012-01-15
You now show the Windows boot loader in the MBR. Does it boot Windows directly? Or do you have to press f8 to get into repairs to make it work?

Boot repair showed this:
> The file system wasn't safely closed on Windows. Fixing.Did you hibernate in Windows and then use Linux. That can often cause problems.

To boot Ubuntu you will have to reinstall grub2's boot loader to the MBR. I think boot repair will fix that.

---

### Post by tofoko on 2012-01-15
> **oldfred said:**
> You now show the Windows boot loader in the MBR. Does it boot Windows directly? Or do you have to press f8 to get into repairs to make it work?

Boot repair showed this:
Did you hibernate in Windows and then use Linux. That can often cause problems.

To boot Ubuntu you will have to reinstall grub2's boot loader to the MBR. I think boot repair will fix that.

When i start the notebook it will hang on a blinking "-" sign. The loader doesn't work right now because i tried to reinstall ubuntu and i was to slow to install the ATI drivers. But before that, the notebook started in bootloader menu. From there i can choose ubuntu with different settings, and "Windows 7 (loader)" if i choose the "Windows 7 (loader)" option, it just reloads the bootloader.

I am still able to lunch windows with a windows 7 recovery disk.

With the Boot-Rapair-Disk i can get the info to paste.ubuntu.com, but the automatic repair function does not go any where. It been on for 40 min and nothing happens. There are not even any HDD activity

---

### Post by oldfred on 2012-01-15
Often then Windows needs chkdsk or other repairs.

Some have gotten to the Windows repair screen from grub. But had to be quick to press f8 just after pressing the Windows entry in grub2's menu. Some said they had to try several times as it is too fast from grub to loading Windows. 

All grub does is chainload to the Windows PBR - partition boot sector just as the Windows boot loader in the MBR does. So Booting Windows and booting Windows from grub really should be the same.

---

### Post by Maximus559 on 2012-01-16
Try using [this]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files") method to reinstall Grub. Worked for me on several occasions.

---

### Post by oldfred on 2012-01-16
From your Windows repair have you run all of the repair commands? The autorepair takes three trys.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

You then have to reinstall grub2's boot loader to the MBR if Windows boots directly without issue.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

