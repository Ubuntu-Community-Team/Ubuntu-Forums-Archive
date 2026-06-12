---
title: "vboxmanage modifyhd resize doesn't work"
date: 2011-03-23
forum: General Help
---

### Post by rva1945 on 2011-03-23
to expand the VM from 2Gb to 10Gb I run the command

vboxmanage modifyhd  .VirtualBox/HardDisks/VMWXP.vdi --resize 10000

I got this

0%...10%...20%.....(etc) ...100%

then I go to Virtualbox and in Storage, IDE primary master I see

WMWXP.vdi (Normal 9.77GB) that's ok, the disk is expanded

then I start the VM, which is a Windows XP, and in My PC, the C: disk is still 1.95GB 

So?

---

### Post by anglican on 2011-03-24
> **rva1945 said:**
> to expand the VM from 2Gb to 10Gb I run the command

vboxmanage modifyhd  .VirtualBox/HardDisks/VMWXP.vdi --resize 10000

I got this

0%...10%...20%.....(etc) ...100%

then I go to Virtualbox and in Storage, IDE primary master I see

WMWXP.vdi (Normal 9.77GB) that's ok, the disk is expanded

then I start the VM, which is a Windows XP, and in My PC, the C: disk is still 1.95GB 

So?The additional space you've added is not yet allocated. You have two options, you can either use the disk management from within Windows to format the extra space as e.g. D: or you can boot your VM from an iso of [gparted]("http://gparted.sourceforge.net/download.php") and use that to resize the C: partition to use the extra space.

H

---

### Post by rva1945 on 2011-03-24
> **anglican said:**
> The additional space you've added is not yet allocated. You have two options, you can either use the disk management from within Windows to format the extra space as e.g. D: or you can boot your VM from an iso of [gparted]("http://gparted.sourceforge.net/download.php") and use that to resize the C: partition to use the extra space.

H

Do I have to boot from tha iso in WXP guest or Linux Host?

Do I have to burn it into a CD?

---

### Post by timgood on 2011-03-24
Download the iso and then select it in the VB settings for your guest OS. Boot from the iso (you don't need to burn a physical disk). Resize the partition and Robert should be your father's brother.

---

### Post by rva1945 on 2011-03-24
> **timgood said:**
> Download the iso and then select it in the VB settings for your guest OS. Boot from the iso (you don't need to burn a physical disk). Resize the partition and Robert should be your father's brother.

I'm downloading the iso, but still have'nt found how to tell the VM that it can boot from that iso. There's a boot menu accessible by pressing F12 while the Vm is booting, but the options are

Floppy
CD-ROM
HD Network

Where do I place the iso file?

---

### Post by rva1945 on 2011-03-24
> **timgood said:**
> Download the iso and then select it in the VB settings for your guest OS. Boot from the iso (you don't need to burn a physical disk). Resize the partition and Robert should be your father's brother.

Ok ok, I added the virtual CD image, booted form the gparted iso and resized the HD. Apllied changes and everything was successfull. Now (after removing the virtual CD), Wxp is gone, the VM doesn't boot.

Did I lost the Wxp VM?

---

### Post by timgood on 2011-03-25
> **rva1945 said:**
> Ok ok, I added the virtual CD image, booted form the gparted iso and resized the HD. Apllied changes and everything was successfull. Now (after removing the virtual CD), Wxp is gone, the VM doesn't boot.

Did I lost the Wxp VM?

You probably just need to point the VM at the new disk image - it is still looking for the old one. Find that under IDE Primary Master, and point it at the .vdi file. Then reboot.

---

### Post by rva1945 on 2011-03-25
> **timgood said:**
> You probably just need to point the VM at the new disk image - it is still looking for the old one. Find that under IDE Primary Master, and point it at the .vdi file. Then reboot.

I go to settings of the VM, in Storage, under IDE controller I see the WMWXP.vdi file which is the disk I need to enlarge. In VIrtual Size it says 9.77 GB, in Actual Size, 1.53GB. That's the disk I resized using GParted.

If I click on Setup the virftual hard disk, that is selected.

But the file as seen in nautilus is still 1.5GB in size!

And when I start the VM, it doesn't boot, just a black screen, with no OS (that's why I think that GParted wiped the disk).

I'd appreciate any help.

---

### Post by timgood on 2011-03-25
After you resized the disk image, did you make the partition active and bootable? This may be the problem. Reboot from the .iso and check the partition settings.

---

### Post by timgood on 2011-03-25
I've just resized my Win XP .vdi from 10GB to 20GB successfully. I noticed that after the resizing of the disk image, the partition appeared to be empty. However, choosing 'check the partition for errors' refilled the missing data. After I restarted, XP chkdsk autoran and then everything was fine.

---

### Post by timgood on 2011-03-25
> **rva1945 said:**
> 
But the file as seen in nautilus is still 1.5GB in size!


Yes, because the file size changes dynamically as you add data.

---

### Post by rva1945 on 2011-03-25
> **timgood said:**
> After you resized the disk image, did you make the partition active and bootable? This may be the problem. Reboot from the .iso and check the partition settings.


IN GParted, I see the partition with the new size, in the last column, it says boot.

But anther thing I don't understand is the fact that in VB the virtual size is almost 10GB, but the vdi file remains at 1.5GB

---

### Post by timgood on 2011-03-25
> **rva1945 said:**
> 
But anther thing I don't understand is the fact that in VB the virtual size is almost 10GB, but the vdi file remains at 1.5GB

See my previous answer. The virtual size is the maximum size of the disk. The actual size is the amount of data you have in it. This will expand as data/programs are added. Is there data shown in the partition (i.e is 1.5GB of it shown as being used)? Have you checked the partition for errors as I suggested earlier?

---

### Post by SteveCut on 2011-05-26
If you are configuring a Windows guest then a far simpler solution than using gparted is to download (in the Windows VM) the free Easeus Partition Manager and simply resize the partition.

---

