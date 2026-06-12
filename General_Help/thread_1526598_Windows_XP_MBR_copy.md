---
title: "Windows XP MBR copy"
date: 2010-07-08
forum: General Help
---

### Post by neo.patrix on 2010-07-08
Hi all,

I need to execute a complex scenario for Master Boot Record swapping, which is described as follows

System Spec : Dual boot System

1) Ubuntu Linux 10.04 
2) Windows XP Home Edition

My "fdisk -l output is 

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        2034    16289910    7  HPFS/NTFS
/dev/sda3            2035        2839     6466162+  83  Linux
/dev/sda4            2840       14593    94414005    f  W95 Ext'd (LBA)
/dev/sda5            2840        8645    46636663+   7  HPFS/NTFS
/dev/sda6            8646       12214    28667961   83  Linux
/dev/sda7           12215       14354    17189518+  83  Linux
/dev/sda8           14355       14593     1919736   82  Linux swap / Solaris


``` 

"parted /dev/sda" & print -

```

Model: ATA WDC WD1200BEVS-7 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16
 2      49.4MB  16.7GB  16.7GB  primary   ntfs            boot
 3      16.7GB  23.4GB  6621MB  primary   ext3
 4      23.4GB  120GB   96.7GB  extended                  lba
 5      23.4GB  71.1GB  47.8GB  logical   ntfs
 6      71.1GB  100GB   29.4GB  logical   ext3
 7      100GB   118GB   17.6GB  logical   ext3
 8      118GB   120GB   1966MB  logical   linux-swap(v1)


```

1) Copy my current DualBoot MBR which uses grub

2) Restore original MBR which Windows XP writes during system installation. I know there is a Windows Restore Utility known
as "fixmbr" which could do the job.

3) Make a copy of Windows XP default MBR same as DualBoot MBR

4) Restore my DualBoot grub configuration back to normal 

Thanks in advance

---

### Post by endotherm on 2010-07-08
you can also write the windows mbr in linux with the ms-sys package. its no longer in the repos but you can find it here:
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

here are some instructions I've used in past:
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

if you actually want to backup the mbr rather than write a new one, most people use dd to slurp off the first sector of the active partition like so (this assumes sda is your active disk, which yours appears to be)
```

dd if=/dev/sda of=~/mbr.img bs=512 count=1
```more info here:
[http://www.backuphowto.info/backup-mbr-linux](http://www.backuphowto.info/backup-mbr-linux)

be very careful with dd. it can really mess stuff up if  misused.

one last thing to consider is that there isn;t really a "dualboot" mbr, but  just one that points to grub and another to ntldr/bootsec. the boot loader (be it grub or ntldr/bootsec) configuration handles things like boot images. there really  isn't much in the mbr to mess up except the address to which it points.  with windows often after altering the mbr, you must also run a command  known as fixboot, to ensure that your ntldr/bootsec.dat is being pointed to  from the mbr.

---

### Post by neo.patrix on 2010-07-08
Thanks endotherm.

I need this command sequence verified before execution. Of-course all risk is mine, but still I am dealing with boot-loader here.

1) Rewrite MBR for Windows XP direct boot (without grub)

```
ms-sys -m /dev/sda
```

2) Create a copy of MBR pointing to XP bootsec 

```
dd if=/dev/sda of=~/mbr.img bs=512 count=63
```

3) Restore good old grub

```
update-grub
```

Does ms-sys have something like dry-run , where output can be directed to a file ? I would prefer not to play around with MBR just to use "dd".

Thanks

---

### Post by oldfred on 2010-07-08
If you use blocksize of 512 you are including the partition table. And then if you install to another drive you destroy the partition table on that drive use 446 if you just want MBR boot portion.

I think it is easily just to reinstall boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you have windows disk you can run the fixMBR command.

If you can boot into your Ubuntu install just install grub to another drive from the working install. Slightly easier than using liveCD.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by endotherm on 2010-07-08
> **neo.patrix said:**
> Thanks endotherm.

I need this command sequence verified before execution. Of-course all risk is mine, but still I am dealing with boot-loader here.

1) Rewrite MBR for Windows XP direct boot (without grub)

```
ms-sys -m /dev/sda
```2) Create a copy of MBR pointing to XP bootsec 

```
dd if=/dev/sda of=~/mbr.img bs=512 count=63
```3) Restore good old grub

```
update-grub
```Does ms-sys have something like dry-run , where output can be directed to a file ? I would prefer not to play around with MBR just to use "dd".

Thanks

I'm with you up to step 3. I don;t know if update-grub will cause the mbr to be rewritten. I've only ever used it for applying changes to the grub.cfg. if you are not sure it will work, then my recomendation is to save the grub mbr with dd, then apply the windows mbr, back it up, and then reapply your backed up grub mbr. 

what exactly are you trying to do? configure which os will load by default after a remote reboot?

---

### Post by The Cog on 2010-07-08
> **endotherm said:**
> I'm with you up to step 3. I don;t know if update-grub will cause the mbr to be rewritten. I've only ever used it for applying changes to the grub.cfg. if you are not sure it will work, then my recomendation is to save the grub mbr with dd, then apply the windows mbr, back it up, and then reapply your backed up grub mbr. 
Well spotted. But this command:
```
grub-install /dev/sda
```
reinstalls grub as the bootloader. I've used it occasionally.

---

### Post by neo.patrix on 2010-07-08
Thanx guys,

I did recognize after further reading that step 3, should grub-install

I need a replica of my OEM installed Windows to be used with VM-Player but that needs proper MBR section as well. 

Problem started with Checkpoint SecureClient, which has no good Linux alternative. I like working with Ubuntu tools but everytime I need to
access my server, I have to reboot to windows for uploading files to server. Since OEM Windows XP, I though it would be best to have replica rather work in VM-Player.

---

### Post by NFblaze on 2010-07-09
Actually, use the first **446 bytes** for just the MBR.

I just spent 5 hours restoring a friends computer, because I dd'd 460.

---

### Post by neo.patrix on 2010-07-09
> **NFblaze said:**
> Actually, use the first **446 bytes** for just the MBR.


Can you please give me appropriate "dd" command ? Thanx

---

### Post by The Cog on 2010-07-09
> **NFblaze said:**
> Actually, use the first **446 bytes** for just the MBR.

I just spent 5 hours restoring a friends computer, because I dd'd 460.

Ooh, bummer!

to take a copy of the existing MBR:
```
sudo dd if=/dev/sda of=/root/MBR-IMAGE bs=446 count=1
```and to restore the image to the drive:```
sudo dd if=/root/MBR-IMAGE of=/dev/sda
```

Use those commands thoughtfully. A typing error can lead to disappointment.

The dd arguments are:
if= - Input File, which can actually be a raw hard disk
of= - Output File - where to copy the input to
bs= - Block Size - how many bytes to copy in one block
count= - how many blocks to copy

---

### Post by neo.patrix on 2010-07-09
I had already risked my neck before your post, but Thanx. 

I did get Windows XP MBR based on a [Running-a-Windows-partition-in-VMware]("http://imrannazar.com/Running-a-Windows-Partition-in-VMware") with slight modification.

Finally, I have used following steps,

0) sudo -i

1) ms-sys -m /dev/sda

2) dd if=/dev/sda of=WindowsXP.mbr bs=512 count=63 

3) grub-install /dev/sda

4) update-grub.

WindowsXP.mbr also working as expected. Still, I do not understand "dd". (I hope not to touch it for a long long time)

PS : My system is still bootable & alive , thanks guys.

---

### Post by endotherm on 2010-07-12
dd is direct disk access, so you are reading or writting the disk on a very very basic level, well below the concept of files and folder hierarchies. there aren't even file systems at that level, just partitions and bytes of data.

---

