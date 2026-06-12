---
title: "need urgent help to repair Grub boot loader"
date: 2012-04-26
forum: General Help
---

### Post by rvboutin on 2012-04-26
Hi,
I did upgrade today from Ubuntu 11.10 to 12.04LTS, everything went pretty much fine except that my Grub menu got messed-up, and I all entries were in duplicate or triplicate (Ubuntu, Windows XP, recovery mode, etc..) so not very practical.
I used Grub Customiser to remove the duplicate/triplicate entries in the Grub Menu as I did before; **problem: **I probably unchecked something by mistake because on reboot all Linux entries were gone from the Grub menu.
I did try the Boot-Repair tool from a LiveUSB Ubuntu, and let everything by default (OS to boot by Default Ubuntu 12.04 on sd5) **and I did not change any other options** in the Grub location and I think that might be the problem... I am now left with just the 2 MEM tests available in the list and Ubuntu and Windows XP are gone!
Basically, I have 1 internal HDD with:
[LIST]
[*] a hidden FAT32 Dell recovery partition that I don't use;
[*] Windows XP SP3 on 1 primary NTFS partition;
[*] Ubuntu+swap on an extended partition (if I remember correctly Ubuntu is on sd5 and swap on sd6).
[/LIST]
My question is very simple... on which partition should I reinstall Grub with Boot-Repair (i.e. which options should I change from default and use?).

Shall I use Super Grub2 Disk 1.99 beta 1 instead of Boot-Repair?

Thank you in advance for your help!

---

### Post by VMC on 2012-04-26
Grap [boot_into_script]("http://sourceforge.net/projects/bootinfoscript/") and boot from any livecd then run the bootinfoscript from root. A RESULTS.txt file will show you what is the MBR pointing to. It will also show the grub.cfg file

---

### Post by lilmagnus on 2012-04-26
You could refer to [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). In most cases Grub is installed to the disk and not a specific partition. In your case the disk is **/dev/sda**.
You could also refer to [this]("https://help.ubuntu.com/community/Grub2") as it contains useful info on how Grub works and commands which can be run to fix issues.

---

### Post by rvboutin on 2012-04-26
Hi,
Thanks for your prompt reply.
Could you clarify "what is the MBR pointing to"... Since I have done a previous repair that failed, would that info be correct?
And the "what is the MBR pointing to" info... how can I use it? what should it look like?
Cheers,
Rv

---

### Post by rvboutin on 2012-04-26
Hi,
Thanks lilmagnus for your reply, I already looked at these websites, but found them quite complicated, is there no ways of restoring Grub configuration to its previous states? Even if that means going on my Ubuntu partition and files to recover an old version of the Grub configuration file (if it still exists since I already repaired (i.e. reinstalled) Grub once...
Cheers,
Rv

> **lilmagnus said:**
> You could refer to [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). In most cases Grub is installed to the disk and not a specific partition. In your case the disk is **/dev/sda**.
You could also refer to [this]("https://help.ubuntu.com/community/Grub2") as it contains useful info on how Grub works and commands which can be run to fix issues.

---

### Post by rvboutin on 2012-04-26
to clarify my questions based on the reply so far, I think the 1st Boot-repair placed Grub on sd5... should it be on dev/sda?
Cheers,
Rv

---

### Post by oldfred on 2012-04-26
When we say we are installing grub to the MBR, we are using shorthand notation. We mean the boot loader portion of the grub2 code. It has to know where the rest of the grub2 code is. All the rest of the grub2 code is in the Ubuntu install.

All BIOS based computers have to have a bit of code in the MBR, BIOS tells computer to jump to MBR. But MBR is small and just has enough code to jump somewhere else to continue to boot. And then the bit of grub in the MBR jumps to the rest of the grub code to load a menu and continue booting. 

Windows boot loader in the MBR, jumps to the partition boot sector which has a bit more code for Windows, which then jumps to more code in Windows.

The MBR is the very first sector of a hard drive. Linux refers to drives as sda, sdb etc. And it refers to the first partition of drive sda as sda1. So partitions have a number after the drive letter.

You have to have a boot loader in the MBR or first sector of drive sda if you tell BIOS to boot from sda. If you install it elsewhere there is no way to get to it. And if you have an old boot loader still in the MBR it does not know where to go.

Boot-Repair is one of the easiest way to fix the MBR as it will install a correct grub2 boot loader to the MBR if it can. If not you can run the bootinfo script which will let use analyze your system and maybe see what is wrong.

---

### Post by rvboutin on 2012-04-26
Thanks oldfred for the explanation!!
So I guess that I have to check that Boot-Repair place Grub on sda and not sda5 as I think it was configured to...
I'll try to press "Left-Shift" first on next reboot (do you think that will work?) to see if I can boot in Ubuntu and fix Grub from there with Grub Customiser.

---

