---
title: "dd command?"
date: 2010-05-11
forum: General Help
---

### Post by jdmBlue on 2010-05-11
Does the following command work in a terminal or where is this command to be placed?


dd if=/dev/sda of=/mbr.bin bs=446 count=1

---

### Post by Ozymandias_117 on 2010-05-11
In a terminal. But, may I ask, what is this supposed to be doing?

---

### Post by jdmBlue on 2010-05-11
Master Boot Record backup. I have Ubuntu and want to dual boot Windows 7. This is a required step.

---

### Post by Lightstar on 2010-05-11
> **jdmBlue said:**
> Master Boot Record backup. I have Ubuntu and want to dual boot Windows 7. This is a required step.

I never did anything like that.

If you have windows first, then install ubuntu, it will detect the partition, grub will work fine out of the box.  (or at least it should, and did for me)

when I have ubuntu first, and then install windows, I usually just reinstall grub from the live-cd after windows replaced the mbr with it's own.  I'm a bit scared of the dd command, especially when it's dealing with mbr

---

### Post by jdmBlue on 2010-05-11
These are the steps.

**Master Boot Record backup and re-replacement**

 Back-up the existing MBR, install Windows, replace your backup overwriting the Windows boot code: 

[LIST=1]
[*]Create an NTFS partition for windows (using fdisk, GPartEd or whatever tool you are familiar with) 
[*]Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1 
[*]Install windows 
[*]Boot into a [LiveCD]("https://help.ubuntu.com/community/LiveCD") 
[*]Mount your root partition in the LiveCD 
[*]Restore the MBR e.g. dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1 
[*]Restart and Ubuntu will boot 
[*]Setup grub to boot windows 
[/LIST]
 
[B]
[/B]

---

### Post by jdmBlue on 2010-05-11
Yes that is why I`m reluctant to do that just yet. I`m checking all options first.

---

### Post by Ozymandias_117 on 2010-05-11
If you have a Windows disk, or can get hold of one, I would strongly suggest against trying that... While the direction it's going for the backup shouldn't cause problems, I would be afraid to try to restore with it...

---

### Post by tgm4883 on 2010-05-11
> **jdmBlue said:**
> Does the following command work in a terminal or where is this command to be placed?


dd if=/dev/sda of=/mbr.bin bs=446 count=1

Wouldn't /dev/sda be the entire drive?

---

### Post by jdmBlue on 2010-05-11
> **tgm4883 said:**
> Wouldn't /dev/sda be the entire drive?

I`m not sure but I`ll check before I proceed with that step. Perhaps it should be 
/dev/sda1 or whatever the Ubuntu partion is?

---

### Post by jdmBlue on 2010-05-11
> **Lightstar said:**
> I never did anything like that.

If you have windows first, then install ubuntu, it will detect the partition, grub will work fine out of the box.  (or at least it should, and did for me)

when I have ubuntu first, and then install windows, I usually just reinstall grub from the live-cd after windows replaced the mbr with it's own.  I'm a bit scared of the dd command, especially when it's dealing with mbr



To do this do I just follow the steps I previously mentioned ?...except do not backup and reinstall MBR?

---

### Post by marshmallow1304 on 2010-05-11
> **tgm4883 said:**
> Wouldn't /dev/sda be the entire drive?

Just the first 446 bytes.


In any case, it's probably easier to just re-install grub.

---

### Post by bananas4370 on 2010-05-11
> **tgm4883 said:**
> Wouldn't /dev/sda be the entire drive?

The MBR is 512 bytes long, and is in the first sector of the hard drive. The command used has bs=446 and count=1. So dd will take /dev/sda as the input, and write the first (count=1) 446 bytes (bs=446) to the output mbr.bin

The other 66 bytes is the partition table. If you backed up the whole 512 bytes and changed your partitions, upon restoring with dd, the MBR would be out of sync.

Hope this helps

---

### Post by Ozymandias_117 on 2010-05-11
Deleted by Author. Missed the previous posters answer, which made mine just a repeat :D

---

