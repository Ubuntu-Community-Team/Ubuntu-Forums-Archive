---
title: "GRUB Problem? (Pictures Included)"
date: 2012-07-24
forum: General Help
---

### Post by dg1598 on 2012-07-24
Hello, sorry if this has already been posted but I can't find it at all!

Anyway, anytime I try to boot into Ubuntu (Dual boot on Compaq Laptop - Windows 7 Ultimate 32bit if that helps) I get these error messages!

[http://postimage.org/gallery/5bd9rgq/657c387d/](http://postimage.org/gallery/5bd9rgq/657c387d/)

I've booted into a Live CD, and used Boot-Repair, just the recommended settings and still no luck! Any help would be greatly appreciated! I can't just reinstall it either because I have important files on it  ](*,)

Thanks, Dylan.

---

### Post by Quackers on 2012-07-24
Did the boot-repair tool give you a link to pastebin? If so please post that link. If not, please run it again and make a note of that link and post it here. That will give details of what is where on your system.

---

### Post by Bucky Ball on 2012-07-24
+1 to Quackers. And always in hindsight: The perfect case for having a separate /home partition (or symlinks in your /home directory in / which are linked to a directory on another partition, best case scenario, on another drive - my new preferred method, thanks oldfred). ;)

Just looked at your screen shot. What happens when you type 'exit' at the grub prompt, then 'startx'? Could you also type 'exit' at the grub prompt then issue these three commands and post the output, please:

```
sudo blkid
sudo fdisk -l
nano /etc/fstab
```

The last one shows you the contents of a file (fstab). This file controls what happens with partitions at boot. Three questions:

Was this install up and running fine previously?
What release have you installed?
Have you just installed and are trying to boot in for the first time?

If the latter, could be an install gone wrong. If you installed correctly then the grub is there somewhere (in the MBR on sda or on the partition that you installed Ubuntu on to probably) and Boot Repair should have found something.

You didn't do a wubi install *inside* Windows by any chance?

---

### Post by dg1598 on 2012-07-25
Hello and thanks for the help from both of you! I did an install through windows yes, with Wubi, the install was working great for around a month or two, but I didn't boot into ubuntu for around 2 weeks when I was on a break, and when I came back I have kept getting GRUB screen! 

the link from Boot-Repair is;
[http://paste.ubuntu.com/1109188/](http://paste.ubuntu.com/1109188/)

I will try the commands said and come back to you, and to answer your questions Bucky,
The install ran perfect previously,
I believe it is 11.04,
No I have booted into it many times,
also, as stated previously I did the install through Windows, I do not know if thats a good or bad thing! #-o

I'm very nooby with ubuntu, and I barely know how to use it but I only use it to allocate more RAM to my server, because I have 32bit Windows installed and it will only let you allocate up to 1gb on that. 
Thanks again for your help and I'll get back to you's with the commands :)

---

### Post by oldfred on 2012-07-25
You have Windows and wubi, but you seem to have left overs from a gpt table also which probably is not related to the wubi problem but would be if you try a full partitioned install.

First backup partition table
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I do not know wubi that well but perhaps a fsck on the wubi install? From LIveCD or USB:

#wubi fsck:
sudo mkdir /media/win
sudo mount /dev/sda2  /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

---

### Post by bcbc on 2012-07-25
See this: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

You need to run chkdsk and maybe afterwards fsck. But start with chkdsk.

The root.disk should be included in the list below.

> sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

PS I'm surprised you could even install with the GUID partition table info present... maybe it's not a problem when you install with wubi.exe standalone (it uses a pre-installed image) but the install that uses ubiquity will always fail.

But I think the problem is likely ntfs corruption based on the root.disk not appearing in that file list.

---

### Post by crownstar on 2012-07-25
I d/led Comodo Rescue Disc which utilizes SliTaz GNU/Linux for LIve CD 
Everytime I reboot with CD in drive it boots up and goes through the process.

then it says something like : Switching to NoHz Mode 
then ACPI Exception : AE_NOT_FOUND
then ACPI No dock devices found
then ACPI : PCI Interrupt Link
then complete Total LOCKUP with GREEN SCREEN : 

vgaarb : device added PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none

My system is : 
MS Windows 7 Home Premium 64-bit SP1
Specification   AMD Phenom(tm) 9850 Quad-Core Processor
HP LP2465 (1920x1200[at]59Hz)
2048MB GeForce GT 520 (XFX Pine Group)

Version   4.2.0
Vendor   NVIDIA Corporation
Renderer   GeForce GT 520/PCI/SSE2

possible video collision driver issue ? 

Regards,
Crown

---

### Post by Bucky Ball on 2012-07-25
Can't see that Boot Repair would do anything for the Ubuntu install as you don't have a hard drive install of Ubuntu, but a Wubi one, installed inside Windows, and therefore no grub anyhow I wouldn't imagine.

I can't help with Wubi, never use it, but you do realise that it is not a long term solution but more designed for people to try Ubuntu for awhile and see if they like? A hard drive install is different and better. I wouldn't bother about fixing this if you've already been using it for a couple of months and like it. Just dual-boot or run one of the OSs as a guest OS inside the other using Virtualbox. Oldfred will be good value to help you fix the underlying problem with gpt. Better user experience with a full install. 

Have fun. ;)

* Wubi installs Ubuntu in Windows just like you would install any other Win app. It is not an install of an OS to a partition, as such, but like installing Photoshop or your favourite game. Many of the fixes you have found will likely not work as they are for a hard drive install, a different fish to a Wubi one (I don't know why the team bother with Wubi as new users can find it problematic and confusing, and besides, people can run Buntu from the disk to try it).

---

### Post by crownstar on 2012-07-25
Attempt running through Xboot / QEMU 
 TEXT MODE : 

oRCU-based detection of stalled CPUs is disabled.
NR_IRQS:512
Console: colour VGA+ 80x25
console [tty0] enabled 
Fast TSC calibration failed 
TSC: Unable to calibrate against PIT
TSC: using PMTIMER reference calibration
Detected 2511.589 MHz processor.
Calibrating delay loop (skipped), value calculated using timer frequency.. 
502317 BogoMIPS (lpj=2511589)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 512
Performance Events: Broken PMU hardware detected, software events only.
Checking for popad bug...OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 32k freed
ACPI: Core revision 20101013
Enabing APIC mode: Flat. Using 1 I/O APICs
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
..MP-BIOS bug: 8254 timer not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A ...
....(found apic 0 pin 2) ...
........ failed.
...trying to set up timer as Virtual Wire IRQ ...

---

### Post by Bucky Ball on 2012-07-25
> **crownstar said:**
> Attempt running through Xboot / QEMU 
 TEXT MODE : 

oRCU-based detection of stalled CPUs is disabled.
NR_IRQS:512
Console: colour VGA+ 80x25
console [tty0] enabled 
Fast TSC calibration failed 
TSC: Unable to calibrate against PIT
TSC: using PMTIMER reference calibration
Detected 2511.589 MHz processor.
Calibrating delay loop (skipped), value calculated using timer frequency.. 
502317 BogoMIPS (lpj=2511589)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 512
Performance Events: Broken PMU hardware detected, software events only.
Checking for popad bug...OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 32k freed
ACPI: Core revision 20101013
Enabing APIC mode: Flat. Using 1 I/O APICs
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
..MP-BIOS bug: 8254 timer not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A ...
....(found apic 0 pin 2) ...
........ failed.
...trying to set up timer as Virtual Wire IRQ ...

? Not sure what this has got to do with anything on this thread ... enlighten me. ;)

---

### Post by dg1598 on 2012-07-26
I used Wubi once I think? But I have 2 partitions on my HDD, one with Linux and one with Windows, and on startup it tells me to select either ubuntu or windows so I'm quite confused when you say that it is installed like any other application such as photoshop? I really can't remember which I used, because I used Wubi once, and I also used the LiveDisk, I am very nooby with this so I honestly don't understand half of your replies! Should I boot up the live disk and type in the commands I was given into terminal? Thanks :)

---

### Post by sorooshubu on 2012-07-26
I think your grub is gone,
please boot with livecd
open terminal
and enter following commands, and send output of these back here.
sudo fdisk -l

---

### Post by bcbc on 2012-07-26
> **sorooshubu said:**
> I think your grub is gone,
please boot with livecd
open terminal
and enter following commands, and send output of these back here.
sudo fdisk -l

Look at the bootinfoscript results. The fdisk output is there already.

---

### Post by sorooshubu on 2012-07-26
> **bcbc said:**
> Look at the bootinfoscript results. The fdisk output is there already.
Oh, it's more than grub problem, where is root partition?
I do not know wubi well, I think some wubi's file in win drive is gone.

---

### Post by Bucky Ball on 2012-07-26
> **sorooshubu said:**
> I think your grub is gone,


This would have been fixed with Boot Repair.

@OP: You don't have Ubuntu installed on the hard drive; Wubi only. All your partitions are NTFS. There are no EXT ones (for Linux).

---

### Post by dg1598 on 2012-07-28
> **Bucky Ball said:**
> This would have been fixed with Boot Repair.

@OP: You don't have Ubuntu installed on the hard drive; Wubi only. All your partitions are NTFS. There are no EXT ones (for Linux).

Oh okay, but still, how do I fix it? I really need to get some server files off Ubuntu! If there is even anyway to access the files on it without fixing it? All I need is to be able to move a folder from my Ubuntu desktop onto my windows desktop?

---

### Post by oldfred on 2012-07-28
Did you run the chkdsk from Windows & fsck from Ubuntu. If you have file issues it may not mount.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

