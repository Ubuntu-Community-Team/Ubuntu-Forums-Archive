---
title: "GRUB Error 22 Problem"
date: 2010-06-20
forum: General Help
---

### Post by Dan09 on 2010-06-20
Hey all, I was wondering if anyone knows how I can go about fixing a Error 22 message that I am getting upon startup after my partition containing my Ubuntu installation was deleted this weekend on my Win7 dual boot PC.

I would simply use a Win7 recovery CD to enter the "fixmbr" command and get everything working again, but my CD burner on my other computer seems to have crapped out, and I'm unable to make a repair CD... 

Here is the output of fdisk -l run from a Ubuntu LiveCD :

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdef690fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288000    7  HPFS/NTFS

Disk /dev/sdb: 2031 MB, 2031091712 bytes
63 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

```Does anyone have any idea on what I should be doing?  Thanks!

---

### Post by Dan09 on 2010-06-20
Anyone at all? I'm getting desperate here :(

---

### Post by oldfred on 2010-06-21
In 20/20 hindsight it would have been better to fix the problem before deleting Ubuntu.

You have to be able to boot from a CD or USB. If you have an install of Ubuntu you can boot. Also works with just about any rescue disk as they usually have lilo already installed.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by Dan09 on 2010-06-21
> **oldfred said:**
> In 20/20 hindsight it would have been better to fix the problem before deleting Ubuntu.

You have to be able to boot from a CD or USB. If you have an install of Ubuntu you can boot. Also works with just about any rescue disk as they usually have lilo already installed.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Appreciate it!  I just finished the commands and about to reboot to see if everything is hunky-dory now.

Thanks very much for the advice!

---

