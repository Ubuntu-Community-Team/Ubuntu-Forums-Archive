---
title: "How to move a Grub2 partition?"
date: 2011-06-29
forum: General Help
---

### Post by Pipps on 2011-06-29
How to move my Grub2 partition?

**Current partitions**
I currently have the following partitions:
- sdb1	        ntfs	48.83GB		XP
- sdb2	        ntfs	416.84GB	data
- sdb3	        ext4	94.13GB		GRUB2
- unallocated	        465.75GB	---

**Aim**
I would like to move the ext4 partition containing GRUB2 from the middle of the disc to the very end of the disc. This would then allow me to merge the sdb2 and the unallocated area into one large 900GB drive.

**Question**
How do I move this ext4 partition whilst preserving its start address and other relevant info, so that upon booting my MBR will still point directly to it even after it has moved?

**EDIT: Question updated - please see [this post]("http://ubuntuforums.org/showthread.php?p=11001890#post11001890") below.**

---

### Post by regala on 2011-06-29
> **Pipps said:**
> 
**Question**
How do I move this ext4 partition whilst preserving its start address and other relevant info, so that upon booting my MBR will still point directly to it even after it has moved?

do you mean: "How do I move this ext4 partition, without moving it ?"

I don't quite understand...

br,

Mathieu

---

### Post by grahammechanical on 2011-06-29
When you complete this move you will still have three partitions. Is this not true? The ext4 partition will still be sdb3. Will it not? It will still have its unique identifying number. Will it not? So, whether the boot loader in the MBR is pointing to sdb3 or to some long id partition number it should still work.

If the boot loader is GRUB then running the command sudo update grub or sudo update grub2 in a terminal will tell GRUB to look for and record the location of all operating systems. So, that should solve any problem. Do you not think so?

As a matter of curiosity, what is the boot loader. It will help us to give more accurate advice. And what do you have on the sda drive? Just curious.

Once you move the partition it is unavoidable that its start and end address on the disc will be altered. There would be no point in having the power to shrink and expand and move partitions if doing so broke the operating systems on the machine. The key here is the boot loader or the boot order in BIOS, if you are using that to select the OS to load.

Regards.

---

### Post by psusi on 2011-06-29
What do you mean by "grub2 partition"?  You mean you installed with a separate /boot partition?  Why?  You should be able to move them around just fine with gparted.

---

### Post by Pipps on 2011-07-01
Will it achieve the same objective more easily by simply booting into a Ubuntu LiveCD, deleting the current GRUB2 partition, creating a new GRUB2 partition at the end of the disc, and then reinstalling a fresh GRUB2 onto this new partition?

Will GRUB2 then automatically identify the pre-existing operating systems elsewhere on the disc and link to them directly upon being reinstalled?

Will the MBR then in turn automatically point to GRUB2 in its new location?

---

### Post by dino99 on 2011-07-01
you are creating a problem where there is not: dont matter if its the first partition or an other, grub is installed on /dev/sdb by default, not sdbx.

If you want to move it, run into a terminal:

sudo dpkg-reconfigure grub-pc

Otherwise to move partition(s), do it one at a time with either gparted/partedmagic But ALWAYS on non mounted partition(s): so first boot with a livecd, then run the partitioning tool

---

### Post by Pipps on 2011-07-01
I have just used a Ubuntu LiveCD to simply move the GRUB2 partition to the end of the disc. I rebooted and GRUB2 was found and everything booted fine.

I then deleted the second NTFS partition (mentioned above in post 1) and created one big 900GB partition by combining it with the previously unallocated disc space.

However, upon then rebooting again, instead of GRUB2 being found as before, the GRUB2 rescue prompt is presented.

What should I do to restore GRUB2?

---

### Post by psusi on 2011-07-01
Again, what do you mean by "grub2 partition"?  That terminology does not mean anything in common use.  If you mean /boot partition, then you should say that.

What is the error grub gives when it drops you at the rescue prompt?

Also the output from the boot info script ( google should take you right to the sourceforge page it is on ) would be helpful.

---

### Post by ahears on 2011-07-01
> **Pipps said:**
> I have just used a Ubuntu LiveCD to simply move the GRUB2 partition to the end of the disc. I rebooted and GRUB2 was found and everything booted fine.

I then deleted the second NTFS partition (mentioned above in post 1) and created one big 900GB partition by combining it with the previously unallocated disc space.

However, upon then rebooting again, instead of GRUB2 being found as before, the GRUB2 rescue prompt is presented.

What should I do to restore GRUB2?


If you have a Live CD from ubuntu you will boot from it:

> 

Select Recover a Broken system, and enter all data as you would as though you are going to install, (you won't be, and ignore setting up the network). When you are finally prompted; select the partition you want with the active linux partition (- [COLOR=Red]sdb3[/COLOR]            ext4    94.13GB        GRUB2) as the 'root file system', and reinstall the grub, and reboot.
That's it. Here are some links below that may help.

---

