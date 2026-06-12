---
title: "Ubuntu and Windows Problem"
date: 2012-04-20
forum: General Help
---

### Post by camshot on 2012-04-20
Hey guys I am Using Windows but I ****** my Windows that hard up that I can't live with it anymore and now I have to format my hard drive, but with Windows on it I can't install it and now my question as Windows is uninstalled and my hard drive is totally formatted can I install Ubuntu without any problems?
I already got Ubuntu installed on my hard drive but then I uninstalled it because I wanted to update it in general but now I am sitting on the same Problem as in the beginning...
Here is the thread and a YouTube video about the Problem:

[http://ubuntuforums.org/showthread.php?t=1954738&page=2](http://ubuntuforums.org/showthread.php?t=1954738&page=2)
[https://www.youtube.com/watch?v=wTC8__TPU4c](https://www.youtube.com/watch?v=wTC8__TPU4c)
[https://www.youtube.com/watch?v=gLG6L0NUvQI](https://www.youtube.com/watch?v=gLG6L0NUvQI)

I want to install Ubuntu 11.10.

Cheers

---

### Post by ZekeGraal on 2012-04-20
If the hard drive is formatted, yes of course it should install. As for the videos and threads you gave, you can't install Ubuntu? Does the live CD return any errors/messages?

---

### Post by camshot on 2012-04-20
As you can see in the video no, everything is working fine it just stops at this point...
And on a friends Pc everything worked fine...
Here you can see the Message...
[[IMG]http://img6.imagebanana.com/img/ksju54ru/thumb/Unbenannt4.jpg[/IMG]]("http://www.imagebanana.com/view/ksju54ru/Unbenannt4.jpg")

---

### Post by oldfred on 2012-04-20
Is that booting the liveCD or an Install. What video card do you have? It could be video card or some other setting.

Where is stopped is not showing any errors so it could be what is next or the error was earlier?

---

### Post by for.i.am.root on 2012-04-20
Look at the picture again...

Asking for cache data failed on your Verbatim Store N Go device. Remove it and then try booting.

Might be time to replace it.

---

### Post by camshot on 2012-04-20
I am goint to try it now with a other USB stick just bought it a few days ago.

All my system specs can be fount in the link to the thread above :)

DIT: I am using the live cd(usb)

---

### Post by camshot on 2012-04-20
Nope still the same Error with a different USB stick...

My Stystem:

Motherboard
ASUSTeK Computer INC. P8P67 REV 3.1 (LGA1155)

GPU
1280MB GeForce GTX 570

Ram
8,00 GB Dual-Kanal DDR3 @ 668MHz (9-9-9-24)

CPU
Intel Core i7 2600K @ 3.40GHz

Hard Drive
117GB OCZ-VERTEX3 (SATA)
(Plugged in with a Sata 6G Cable)

---

### Post by tmaranets on 2012-04-20
Try a liveCD or liveUSB to install Ubuntu. "[sdc] Attached SCSI removable disk" maybe your problem.

---

### Post by camshot on 2012-04-20
If you mean that I choose run Ubuntu from this USB, then I already tried it and it didn't worked out... Same error...

I already tried to put the USB in 3.0 ports and in 2.0 ports but nothing changed at all.

If I would know that it is installing for sure if I will format my whole hard drive the I would format it trough my a Windows CD (also a USB (my old one)) and then I would install it trough the Ubuntu USB.

I also tried it to rebuild the bootloader trough my Windows CD with but nothing changed the last time I tried that it worked out fine and Ubuntu was installing but I had to remove it again from my hard disk and 

now I got the same problem again -.-'

---

### Post by oldfred on 2012-04-20
Do not know if it applies to your model or not, reported by different users:

Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

And just about every nVidia requires the nomodeset option to boot.

---

### Post by camshot on 2012-04-20
My hard disk was already on AHCI mode and IDE gave me a blue screen of happiness and I dont know that to do with this "Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!!"

EDIT: Im just going to fomat my whole drive new with a windows usb and the boot from a ubuntu usb anything special I have to know?

---

### Post by oldfred on 2012-04-20
Windows cannot create linux partitions. It also will try to convert to dynamic partitions if you create more than 4, so do not do that. Some of the third party partition tools may work better, but I have always had good luck with gparted.

Is this a newer system with UEFI?

---

### Post by camshot on 2012-04-20
Yes it is with UEFI and I am sitting here with a totally fresh Windows and UEFI is confusing me all the the way :D

---

### Post by oldfred on 2012-04-20
Grub did have a bug where it would overwrite the FAT32 efi partition so after your Windows install back it up, just in case the bug is still there.

It will install to prepared partitions if you boot in UEFI mode from the liveUSB. Or it will install in MBR mode and you have to convert it.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

I do not have UEFI but do have gpt with BIOS. But my new SSD drive I formated with gpt as recommended by the Arch site and created both the efi partition and the bios_grub partition. With BIOS now I am using the bios_grub, but when I transfer it to my new system it will use the the efi partition.

---

### Post by for.i.am.root on 2012-04-21
Great and very thorough advice from Fred with source articles as well. Listen to that guy :-D

---

### Post by camshot on 2012-04-23
Thanks for that answer but I think I have to read it carefully soon because I actually got very much to do with school and can someone write me a pm with the most important info's in German because my English isn't that good...
thanks :D

---

