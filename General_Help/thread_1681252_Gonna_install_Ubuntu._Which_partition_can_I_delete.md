---
title: "Gonna install Ubuntu. Which partition can I delete on this HP laptop?"
date: 2011-02-03
forum: General Help
---

### Post by sirspazzolot on 2011-02-03
So HP was like Hurrdurrdurr let's ship this computer with all four primary partition spots filled, so now I can't install Ubuntu. I'm hoping somebody has an HP and already knows what all these partitions do, so I'm asking now and I'll look into it myself this weekend if I get no answer. :D

```

Name Filesystem Size

C:/ NTFS 445.11 GB
HP_TOOLS FAT32 99 MB
RECOVERY (D:) NTFS 20.36 GB
SYSTEM NTFS 199 MB

```
I wanna keep recovery and C, and I don't know what the other partitions do. Hopefully someone who has an HP here already knows. Thanks in advance!

---

### Post by sirspazzolot on 2011-02-03
Oh, and if anyone can help me with deleting the partition AND getting win7 to keep booting, that would be great. Knowing my luck, I'll delete the partition, win7 won't know what to do, and neither will I.

---

### Post by sirspazzolot on 2011-02-03
Bedtime bump

---

### Post by sirspazzolot on 2011-02-03
Oh, and if anyone needs to email me or whatever, [email]numberlessusername@yahoo.com[/email] will work peachily

---

### Post by recluce on 2011-02-04
> **sirspazzolot said:**
> So HP was like Hurrdurrdurr let's ship this computer with all four primary partition spots filled, so now I can't install Ubuntu. I'm hoping somebody has an HP and already knows what all these partitions do, so I'm asking now and I'll look into it myself this weekend if I get no answer. :D

```

Name Filesystem Size

C:/ NTFS 445.11 GB
HP_TOOLS FAT32 99 MB
RECOVERY (D:) NTFS 20.36 GB
SYSTEM NTFS 199 MB

```
I wanna keep recovery and C, and I don't know what the other partitions do. Hopefully someone who has an HP here already knows. Thanks in advance!

HP_TOOLS - probably HP diagnostics

SYSTEM - Windows 7 can be set up to use a SYSTEM partition that is different from the WINDOWS partition (C:\), after Windows boots, the SYSTEM partition would not be visible. The size of 199MB is exactly right for that use. If that is correct, GPARTED should show this partition is "PRIMARY" and "BOOT"

First of all, use Clonezilla or Acronis to make a backup of all partitions!

The SYSTEM partition cannot be removed, you would have to reinstall Windows to make it work without it.

HP_TOOLS may be removable, I cannot be sure.

Best thing to do: **after you made your backup**, use GParted to do the following:

1.) Delete C:\ /dev/sdx (with x a numeric value between 0 and 3)
2.) Create an extended partition /dev/sdx
3.) Create an NTFS partition of the same size as the deleted C:\ in the extended partition
4.) Restore your data
5.) Resize the "new C:\" to make room for Ubuntu (use GParted or a Windows tool)
6.) Run Windows Recovery console from CD or USB key (hopefully you received a rescue CD or can create rescue media from your system) and let it detect the changed location of your Windows installation and repair accordingly.
7.) After you verify that Windows works again, install Ubuntu in the free space, installing GRUB **only** to the MBR (NOT to your other partitions)

**Note:** Clonezilla can be tricky as far as the partition size is concerned (target partition MUST be equal or larger in size than backuped partition) and if you want to restore to a different target partition, which will be the case here. Instead of /dev/sdx, your new C:\ partition is going to be /dev/sd5 (in all probability), so you would have to manually edit two files in your backup to reflect the new target partition. 

The easy way around this would be to use Acronis, which does not have these limitations. 

Be sure you understand everything and GOOGLE the things that I only mentioned briefly before you do anything but make a backup!

---

### Post by sirspazzolot on 2011-02-04
Can Windows boot from an extended partition? Huh. Didn't know that. I guess I might try to do that. It would just take a heck of a long time though. :(

---

### Post by Quackers on 2011-02-04
Others in your situation have deleted the HP TOOLS partition, then shrunk the C: partition using the Windows Disk Management console, then created an extended partition in the resulting unallocated space. Then you can create as many logical partitions as you want, within that extended partition. Linux systems will boot from within an extended partition. Windows will not do that unless its boot files are in a primary partition.
Before shrinking the C: partition you should defragment Windows at least once and preferrably twice.

---

### Post by coffeecat on 2011-02-04
> **recluce said:**
> First of all, use Clonezilla or Acronis to make a backup of all partitions!

@sirspazzalot, backing up partitions is good advice. Or for making an image of your Windows/NTFS partitions, I can recommend Macrium Reflect Free:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

Although Acronis is excellent, I find Macrium less irritating.

---

### Post by theozzlives on 2011-02-04
> **sirspazzolot said:**
> So HP was like Hurrdurrdurr let's ship this computer with all four primary partition spots filled, so now I can't install Ubuntu. I'm hoping somebody has an HP and already knows what all these partitions do, so I'm asking now and I'll look into it myself this weekend if I get no answer. :D

```

Name Filesystem Size

C:/ NTFS 445.11 GB
HP_TOOLS FAT32 99 MB
RECOVERY (D:) NTFS 20.36 GB
SYSTEM NTFS 199 MB

```
I wanna keep recovery and C, and I don't know what the other partitions do. Hopefully someone who has an HP here already knows. Thanks in advance!

I'm thinking, use clonezilla to backup the hp_tools partition... resize your drive c: WITH Windows Disk Management tool... create an extended partition in the free space... restore hp_tools as a logical drive... install Ubuntu in a logical drive. HP_TOOLS should be sda2.

---

### Post by sirspazzolot on 2011-02-04
Quackers, lemme just say you're like my favorite person ever. You're there pretty much whenever I need help. Thanks.
I already have factory reset disks and a system disk image thing, for the record. I'm reluctant to put HP_TOOLS in an extended partition because I'm afraid I wouldn't be able to use it or whatever. Would I be able to?

---

### Post by JayKay3OOO on 2011-02-04
Or you could save all that and just install it inside windows using wubi. Near as makes no difference performance wise.

Just a thought...

---

### Post by sirspazzolot on 2011-02-04
Wubi is a great tool but I had a bad experience with a wubi install of 9.10. I updated it and everything died. So I've stayed away from it since then.

---

### Post by sirspazzolot on 2011-02-04
Bump again. Parents making me go out to dinner. Bumping purely out of boredom.

---

### Post by sirspazzolot on 2011-02-04
Sigh... bump again. I'll let it die soon.

---

### Post by recluce on 2011-02-05
> **sirspazzolot said:**
> Can Windows boot from an extended partition? Huh. Didn't know that. I guess I might try to do that. It would just take a heck of a long time though. :(

Yes, if there is a primary SYSTEM partition. This has worked since Windows 2000, even though it is little documented. You can even install Windows in this manner, if you do the partition layout before installing Windows.

The SYSTEM partition contains the boot sector, boot manager and a few other files, everything else is on the WINDOWS partition (which can be a logical partition). The layout you posted suggests that your SYSTEM partition might be a Windows SYSTEM partition. If you find bootmgr and a BOOT folder there, it is.

---

