---
title: "I believe my partition table may have been wiped."
date: 2010-09-11
forum: General Help
---

### Post by zetsubouda on 2010-09-11
I started out with 1 XP partition and 1 windows 7 partition.
I replaced my windows 7 partition with an Ubuntu(9.04) partition.
After doing that Grub didn't show up with my XP partition(which it has in the past after installing Ubuntu)
So i tried to change the boot loader and after trying many things may have deleted my partition table, but i'm not sure.

If i boot using UBCD i can boot off of my Ubuntu partition, but i get an error when trying to boot off of my XP partition.

When i load gnome partition manager It says all of my hard drive is unallocated.

If someone could help me with this that would make my week.

---

### Post by srs5694 on 2010-09-11
If I understand correctly, you *are* able to boot your regular disk-based installation, albeit only with the help of UBCD. If so, your partition table is damaged, not destroyed, since there's you couldn't boot from the hard disk if your partition table had been destroyed. Check [my Web page on the topic](http://www.rodsbooks.com/missing-parts/index.html) for information on one common type of problem that produces the "missing partitions" symptom. Post back with the output of "sudo fdisk -lu" (preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility) if you need more help. Note that the partitions issue is likely to be separate from your boot loader problem. Chances are you'll need to re-install your boot loader after you fix your partition table.

---

### Post by zetsubouda on 2010-09-11
I put 
```
 sudo fdisk -lu 
```into my terminal and this is what it spat out

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a6579bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           16065   228990509   114487222+   f  W95 Ext'd (LBA)
/dev/sda3   *   228990510   308688974    39849232+  83  Linux
/dev/sda4       308672910   312576704     1951897+  82  Linux swap / Solaris
/dev/sda5   *       16128   228990509   114487191    7  HPFS/NTFS

```
I'll read your page that you gave me a link for when i get home. I only have a few minutes right now.

---

### Post by srs5694 on 2010-09-11
Unless I've missed something, there's one problem with your disk: Your swap partition (/dev/sda4) begins before the main Linux partition (/dev/sda3) ends. To fix it, I recommend you do the following:


[list=1]
[*]Boot a Linux emergency disk, such as [System Rescue CD](http://www.sysresccd.org/) or [PartedMagic.](http://partedmagic.com) Some of these discs enable you to omit the "sudo" from the below commands.
[*]Disable swap by typing "sudo swapoff /dev/sda4". (This may not be necessary, and could return an error if swap isn't being used.)
[*]Launch fdisk on /dev/sda to edit it (that is, "sudo fdisk -u /dev/sda").
[*]Delete /dev/sda4 using the "d" option in fdisk.
[*]Create a new swap partition using the "n" option in fdisk. It can be either /dev/sda1 or /dev/sda4, but the latter will be slightly less confusing, since it will come after /dev/sda3 in disk space. Start it at sector 308688975 and end it at the default value. That will  probably make it just a bit smaller than the current swap partition. Be sure to give it a partition type ("Id") of 82. (You'll need to use "t" to do this.)
[*]Type "p" to check the partition table. It should resemble what you've got now, except that the swap partition will start slightly later than the current one does, and it may have a different end point, too.
[*]Type "w" to save your new partition table.
[*]If you see a message to the effect that the changes to the partition table won't take effect until you reboot, do so, booting back into your emergency disc.
[*]At a shell prompt, type "sudo e2fsck -f /dev/sda3". (This assumes you're using ext2/3/4 on your main partition; if not, you'll need to use another fsck utility.) This will probably take a while to finish. The intent is to detect and fix any corruption that might have occurred because of the overlapping filesystem and swap partitions. It's conceivable the utility will ask you how to fix damage. If so, select the defaults and hope for the best.
[*]Type "sudo mkswap /dev/sda4" (or change /dev/sda4 to /dev/sda1, if that's where you created your new swap partition).
[*]Reboot into your regular Linux installation.
[*]Type "sudo blkid /dev/sda4" (or whatever the partition ID is for swap) and copy the UUID value into a text editor, or keep it visible on the terminal you're using.
[*]Edit /etc/fstab. Locate the swap line and replace the UUID value with the one from the previous step.
[*]Reboot.
[*]Type "free -m" at a shell prompt and verify that you've got a non-0 "Swap" line. If free shows that you don't have any swap, then something went wrong in the last few steps and you'll have to review and repeat them to get your swap space recognized.
[/list]


Sorry this is a bit lengthy, but the potential for damage to your main Linux filesystem necessitates precautions like checking the filesystem, which needs to be done from an emergency disc (or you could boot into single-user mode with a read-only filesystem, but that's not really any easier).

---

### Post by zetsubouda on 2010-09-12
```

stuart@stuart-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1758        330       1427          0         13        137
-/+ buffers/cache:        179       1578
Swap:         1900          0       1900

```If this is the correct output then the partition table problem is fixed.
I had to change sftab under partition magic because it said I didn't have authorization.

The biggest problem that I have now is that if i don't boot using UBCD my computer says that it doesn't have a boot sector, and I can't boot my XP partition.

---

### Post by oldfred on 2010-09-13
Your only NTFS partition is sda5. Windows combines boot of an extended partition into the install of windows in the primary partition as windows only boots the one primary  partition that is active (boot flag). You also show a boot flag on sda5 but windows will never see it and linux does not use it. You should only have one boot flag per drive.

More info on how windows boots multiple installs. When you deleted win7 you probably delelted the boot files for XP.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by srs5694 on 2010-09-13
The output of free doesn't really tell you anything about your partition table. I included it in my instructions in the earlier post just as a way of verifying that the change to the UUID in /etc/fstab worked. That said, if you deleted the swap space and re-created it, as specified in my instructions, it should be fine, since fdisk won't let you create overlapping partitions. If you want to be absolutely 100% sure, though, you'll need to use "sudo fdisk -lu" again and check that you don't have any overlap in the partitions on your disk.

---

### Post by zetsubouda on 2010-09-13
@srs5604- Thank my partition table appears to have no more overlapping partitions in it :D

@oldfred- If i understand you correctly you want me to make a partition on my hard drive and install a bootloader onto it. If so does the format of the partition matter?

---

### Post by oldfred on 2010-09-13
You have to have a windows install as I understand it in a primary partition to be able to boot the install in a logical partition.

Do not know if you can just put a NTFS primary partition and make it bootable with the boot files? It may be best just to use gparted to copy the partition to a primary partition. Then you may be able to repair it.

---

### Post by zetsubouda on 2010-09-13
@oldfred- I searched how to install a boot loader so now i have grub and don't have to rely on UBCD.
But I still can't boot my xp partition.

partition editor says that it can't read the contents of the file system but if i go to "places" or "computer" i can look at the folders on that partition.

---

### Post by oldfred on 2010-09-13
I have had that issue when the partition needed chkdsk running. I do not know if windows will run its chkdsk on an extended logical partition but it should as it allows data NTFS partitions and second installs in logical partitions.

XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

Run chkdsk several times, until no more errors are detected.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

