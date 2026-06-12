---
title: "Problem booting into Ubuntu 11.10"
date: 2012-04-28
forum: General Help
---

### Post by Jammanuser on 2012-04-28
Ok. I just recently purchased an Alienware M17xR3 laptop which came
pre-loaded with Win7 Ultimate. I wanted to multiboot W7 with Ubuntu and XP, so I went ahead and burned Ubuntu 11.10 to CD, booted from it, and installed it. My plan was to keep the Win 7 boot manager in control of the boot, and use EasyBCD to add a boot entry to chainload Ubuntu's bootloader. So I selected the Ubuntu partition (volume 7, (hd0,6), sda7) as where to install the Grub bootloader. However, during installation, I received an error message saying that the bootloader was not installed. It didn't say why. Note that my hard drive and partition setup looks like this:

(From Dell Configuration Utility loaded when viewing the first screen at startup, by pressing Ctrl + I):
**RAID 0 Volume:** 
M17xRAID0Volume Size: 932 GB

**Physical Disks:**
Port 0  Size: 466 GB
Port 1 Size: 466 GB

(From Win 7 Disk Management)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216777&stc=1&d=1335629636[/IMG]

The 851.74 GB NTFS C: partition contains W7 OS and its programs and settings, of course, and the 9.7 GB NTFS RECOVERY partition is "system" and "active", meaning it contains the boot files of W7 (i.e. bootmgr and boot/bcd). The E: drive is a partition I created for Windows XP, though I have not actually installed Windows XP yet, and the 28.09 GB partition you see is the ext4 formatted partition Ubuntu's installer created and which contains Ubuntu 11.10, while the last partition shown is the 1.91 GB swap partition I created during Ubuntu's installation.

Ok, so now that you have a rough idea of my system layout, I want to ask for advice on how to get the Grub bootloader installed on the Ubuntu partition after-the-fact, when I cannot boot into ubuntu at all. I already created an entry for ubuntu with EasyBCD, but when I select it in the boot menu at startup and press Enter, I just hit a grub prompt which allows you to enter Grub commands. So basically, I just need to know the exact commands to enter which will install Grub to the partition's bootsector (and not to the MBR, as I do not want to overwrite the Win 7 boot manager). Note that I tried using the Super Grub disk for this task (i.e. to install Grub after the installation of Ubuntu which failed to install Grub), but was unable to figure out how to do it since none of the text options seemed to be for that, and attempting to boot the Linux partition from SGD failed since there was no Grub there in the bootsector.

Thanks in advance for any help you can provide with this problem. :)

-Jam Man

:guitar:

---

### Post by Jammanuser on 2012-04-28
UPDATE: Oh, wait...its not a Grub prompt when I select the Ubuntu entry in the boot menu at startup. Its Grub4Dos, which is a big difference of course. I'm not sure, but I don't think Grub4Dos can directly load up the Linux kernel. I need regular Grub or Grub 2 for that, but I don't how to do that after installation, when I cannot boot into Ubuntu.

Any ideas, anyone?

Thanks in advance.

---

### Post by Jammanuser on 2012-04-30
No replies still?? :(

Help!!! Someone...help!!! :lolflag:

A little help over here would be nice.

---

### Post by oldfred on 2012-05-01
Do you want grub2?

I think this works with RAID as it adds the driver.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Otherwise with grub2 you have to specify a partition and use --force. But the liveCD's do not include the RAID drivers, so you have to add those first. I do not use RAID and am not sure what type of RAID you have.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

---

### Post by Jammanuser on 2012-05-01
> **oldfred said:**
> Do you want grub2?

I think this works with RAID as it adds the driver.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Thanks for the suggestion. I created a Boot-Repair CD, and booted from it. At startup, it asked me if I wanted to remove "dm-raid" and replace it with "MDraid", as there might be a conflict. I said no (the first time) and it showed a screen with basically only one option (to create the boot info report). So I did that, and it wanted me to connect to the internet, but I wasn't able to. I clicked the icon on the screen which said "Create VPN connection" or some such thing, and that brought up a dialog box with a Wireless tab, which when I clicked on it, didn't show any wireless networks (so maybe it needs a network card driver?), and so I could not connect. And due to this fact, I could not get on here and post the boot info report. But I did look through it, and saw an error saying it could not read /dev/sda1, so evidently even though it has a RAID driver, it wasn't able to read my RAID system for some reason. It also basically said the same thing
when I ran it again, this time selecting to replace dm-raid with MDraid. 

And so, obviously, that didn't help anything unfortunately... :(
Btw, I don't know much about RAID, and am not sure which kind of RAID type I have (i.e. fakeRAID or real RAID, or whatever), though I know it is RAID 0. Is there some way to find out what kind of RAID I have on my computer?

> 
**Otherwise with grub2 you have to specify a partition and use --force.** But the liveCD's do not include the RAID drivers, so you have to add those first. I do not use RAID and am not sure what type of RAID you have.

Are you talking there about installing Ubuntu again, and selecting to install Grub on the partition? Or are you saying
there is a way to install Grub from the command-line on the LiveCD? If so, what is the commands?
Also note that the LiveCD I have must have a RAID driver, since when I installed it, it was able to read my RAID system just fine. So that indicates to me that there is a RAID driver on the
CD. 
> 
Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
Thanks for the links. I'll have to check them out.

-Jam Man

:guitar:

---

### Post by oldfred on 2012-05-01
You can reinstall grub2's boot loader from a liveCD.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

But with RAID you do not install to sda or even sda1 (a partition) but install to the RAID.

What little I know about RAID, is that RAID 0 is dangerous. And file issue and you lose everything.

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

And if you really need speed a non-raid SSD is much better.

I found this in my notes for an example of the mount. Your device will be different.

For RAID reinstall
ls /dev/disk/* -l
sudo mount /dev/mapper/nvidia_abjcfaad3 /mnt  # where nvidia_abjcfaad3 is partition
sudo grub-install --boot-directory=/mnt/boot /dev/?? # ?? which should be root of raid

This would be a normal partition reinstall, where sda5 is partition with install and sda is drive:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by Jammanuser on 2012-05-03
> **oldfred said:**
> 
For RAID reinstall
ls /dev/disk/* -l
sudo mount /dev/mapper/nvidia_abjcfaad3 /mnt  # where nvidia_abjcfaad3 is partition
sudo grub-install --boot-directory=/mnt/boot /dev/?? # ?? which should be [B]root of raid
[/B]
By "root of raid" you mean Ubuntu partition inside RAID volume, correct? So if the first command shows the following (and it does):

> 
ubuntu@ubuntu:~$ ls /dev/disk/* -l
/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 ata-HL-DT-ST_DVDRW_BDROM_CA30N_K0KBCF45842 -> ../../sr0
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 ata-ST9500423AS_5WR13DX2 -> ../../sdb
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 ata-ST9500423AS_6WS1EEVK -> ../../sda
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume -> ../../dm-0
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume1 -> ../../dm-2
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume2 -> ../../dm-3
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume3 -> ../../dm-4
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume5 -> ../../dm-5
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume6 -> ../../dm-6
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-name-isw_bgajfdadfj_M17xRAID0Volume7 -> ../../dm-7
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume -> ../../dm-0
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume1 -> ../../dm-2
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume2 -> ../../dm-3
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume3 -> ../../dm-4
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume5 -> ../../dm-5
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume6 -> ../../dm-6
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 dm-uuid-DMRAID-isw_bgajfdadfj_M17xRAID0Volume7 -> ../../dm-7
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 scsi-SATA_ST9500423AS_5WR13DX2 -> ../../sdb
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 scsi-SATA_ST9500423AS_6WS1EEVK -> ../../sda
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 wwn-0x5000c50046e76f44 -> ../../sda
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 wwn-0x5000c50048a97c33 -> ../../sdb

/dev/disk/by-label:
total 0
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 OS -> ../../dm-4
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 RECOVERY -> ../../dm-3
lrwxrwxrwx 1 root root  9 2012-05-03 18:01 Ubuntu\x2011.10\x20amd64 -> ../../sr0
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 Windows\x20XP\x20Professional -> ../../dm-5

/dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root 9 2012-05-03 18:01 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 9 2012-05-03 18:01 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root 9 2012-05-03 18:01 pci-0000:00:1f.2-scsi-2:0:0:0 -> ../../sr0
lrwxrwxrwx 1 root root 9 2012-05-03 18:01 pci-0000:13:00.0-scsi-0:0:0:0 -> ../../sdc

/dev/disk/by-uuid:
total 0
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 29ee4b15-5ef5-4183-aeae-3e2294b83f16 -> ../../dm-6
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 3458F7296840D476 -> ../../dm-4
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 C0EB-A839 -> ../../dm-2
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 DA0E9A950E9A69F1 -> ../../dm-5
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 E448F0FD48F0CEF4 -> ../../dm-3
lrwxrwxrwx 1 root root 10 2012-05-03 18:01 eef5fff3-d866-414b-87e1-3f0433b07c9a -> ../../dm-7

I would do:

```

sudo mount /dev/mapper/isw_bgajfdadfj_M17xRAID0Volume7 /mnt
sudo grub-install --boot-directory /mnt/boot /dev/dm-7

```
??

Thanks for the assistance.

---

