---
title: "grub loading, please wait error 22"
date: 2011-04-30
forum: General Help
---

### Post by omrsafetyo on 2011-04-30
So yesterday I applied all updates to my Kubuntu 10.04 installation, and shutdown and went to bed.  Booted up this morning and found:

> 
GRUB Loading stage1.5.


GRUB loading, please wait. . . 
Error 22 


I found that this GRUB error means:
> 
22 : "Must load Multiboot kernel before modules"
This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.


Okay.. simple enough, lets re-install GRUB.  So I booted up my live CD, and ran:
sudo GRUB
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit
sudo shutdown -r now

Same error. :confused:

So I started looking around, and most complaints of this particular error seem to be dual boot environments, which I found rather odd, as I have never dual booted this machine.  I do have a FAT32 drive with a broken Windows installation that crashed back in like 2006 and has since been a data drive; but otherwise when I built this PC, the primary HD was bought off new egg and never had a windows installation.  The FAT32 drive is hooked to a slave IDE channel so that it should never try to boot.  But maybe?

So I rebooted again and went into my BIOS, and brought up the boot sequence.  I went into the Hard Disk Boot Priority and found, lo and behold that the drive attached to slave on Channel 0 was set as the 1st priority boot drive.  Channel 4 Master drive had 2nd priority.  I swapped these around and booted up - good to go!

Just thought I would shar emy experience, as everyone else seemed to be re-installing the MBR to correct their Windows installation - in my case, I'm not trying to recover my Windows installation - thats been broken for years and I don't want it.  However, I find it strange that the BIOS setting would have been modified without me having modified it.  I wonder if anyone has any ideas on that?

---

### Post by oldfred on 2011-04-30
Not sure BIOS changed.

We have seen BIOS that boot mixed PATA/SATA configurations with different drive orders. Do not know but speculated that drives do not always power up the same.

Have seen systems mis-configured with master/slave settings or using old 40 wire PATA connectors with cable select.Weird things then happen.

We have seen external drives inserted as sda or sdf when only one other drive is one system. 

There is very little software that can modify a BIOS, so that did not change unless you changed a setting, reset defaults or moved connectors on motherboard.

---

