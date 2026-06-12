---
title: "Sharing a Drive - Ubuntu and XP"
date: 2006-03-02
forum: General Help
---

### Post by cabber on 2006-03-02
I currently have this configuration:

Windows XP (boot) on a 250G HD SATA
Ubuntu (boot) on 37G HD SATA

I have an extra drive (250G SATA) that I want to be able to share data between the two OS's.  What is the best way to do this?  I've tried to format/partition this drive in XP with the "disk management" tool, but it only gives me the option to create an NTFS partition which I understand will not communicate with Ubuntu.  My understanding is I have to have a FAT32 partition in order for both OS's to see the drive??  Can I create this partition in the Ubuntu OS?  I guess not since it is already formated into an NFTS partition.

Is there something in the Windows "recovery console" that can do this?  Or in the WIndows "disk management" software.  I basically want to make the entire drive a FAT32 drive to store data that both OS's can use.  Thanks

---

### Post by Ramses de Norre on 2006-03-02
Use gparted in ubuntu to reformat it (unmount it first).
You could also make it ext3 and use ext2IFS in windows to add drivers for it so windows can read and write on it.
That works realy good for me and ext3 is certainly superior to fat.

---

### Post by cabber on 2006-03-02
```
 	Use gparted in ubuntu to reformat it (unmount it first)
``` Would you have th etime or be so kind as to walk me through this?  As I am somewhat new to Linux.

```
You could also make it ext3 and use ext2IFS in windows to add drivers for it so windows can read and write on it.
```  Once again, I would love to learn how to do this, but have no clue.  I would need step by step instructions.

First things first:  I have a problem here.  I installed Windows XP on my main SATA drive first.  After I got that up and running, I placed in the 37G SATA Drive and installed Ubuntu.  I got that working fine.  Here's where it gets troubling.

I shut down the machine, and installed the 250G SATA third drive (NTFS partition) and tried to boot into Ubuntu.  The system starts loading the modules and stops with an erro and Ubuntu refuses to boot.  Any idea what the cause is?  Its obvious that this drive is the culprit.  I know it is functioning properly because it boots into WIndows just fine.

---

### Post by aysiu on 2006-03-02
Frankly, I'm surprised XP's disk management allowed you to create only an NTFS format. I was able to create FAT32 partitions in XP.

To format it as FAT32 in Ubuntu, open up a terminal (Applications > Accessories > Terminal) and type this command: ```
sudo fdisk -l
``` It'll list a bunch of partitions. One should be NTFS. Another should be "Linux" (probably Ext3). The third should be unknown.

Let's just say (for this example) that the unknown one is /dev/hda3. To make sure it's unmounted, type ```
sudo umount /dev/hda3
```

To install and use GParted, type ```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
```

GParted is a graphical application, and it's pretty easy to figure out. Let us know if you have questions, though.

[QUOTE=cabber]
I shut down the machine, and installed the 250G SATA third drive (NTFS partition) and tried to boot into Ubuntu.  The system starts loading the modules and stops with an erro and Ubuntu refuses to boot.  Any idea what the cause is?  Its obvious that this drive is the culprit.  I know it is functioning properly because it boots into WIndows just fine.[/QUOTE] You could try reinstalling Grub:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

