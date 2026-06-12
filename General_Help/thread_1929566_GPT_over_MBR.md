---
title: "GPT over MBR?"
date: 2012-02-22
forum: General Help
---

### Post by Shmook on 2012-02-22
While considering installing FreeBSD alongside 7 other Linux distros I learned it recommends using the GPT arrangement of the HDD, especially if you're going to have several bootable OS's. 

After reading more and more about this I'm intrigued but concerned; I also run XP 32, which apparently cannot boot under standard GPT unless you retain an MBR section, which immediately sounds like trouble to me.

My question is your for informed opinions of switching to GPT; the ease (or difficulty) of the reconfiguration, how this would affect programs' behaviors (gparted,etc), and whether it's worth it in the long run. I must say, saying goodbye to extended and logical partitions sounds very nice. Thanks in advance.

---

### Post by oldfred on 2012-02-22
I have gpt on one old drive that I reformated, my new SSD and even on a flash drive just to see if it works. Before SSD I did not have AHCI and gpt worked well dual booting Linux on gpt and XP on MBR but with different drives. Do not attempt on one drive.

But I still have MBR for my XP drive and now with the SSD I have to change BIOS to AHCI. With XP it is difficult to reset to make XP work with AHCI, so I finally was forced to obsolete my XP which I had promised for the last 5 years. (I can boot it but have to change BIOS back each time).

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

The important thing with gpt is to include a small bios_grub partition so grub2 can install correctly.

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

Why you do not want a hybrid MBR/gpt drive.
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

---

