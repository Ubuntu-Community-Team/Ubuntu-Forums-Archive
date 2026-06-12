---
title: "Uninstall Ubuntu and GRUB by installing Windows 7?"
date: 2010-06-10
forum: General Help
---

### Post by roddhall on 2010-06-10
I have my system set up to dual boot Ubuntu 9.10 Karmic Koala and Windows XP Pro, using GRUB 2 (1.97~beta4) as the boot loader. I want to remove Ubuntu and GRUB 2 from the system and install Windows 7 in a dual boot environment with Windows XP. My concern is to be sure that in the process of removing Ubuntu I do not make my system unbootable by removing or otherwise screwing up GRUB without replacing it with the Windows boot loader.
   
  I read a suggestion saying that the most straightforward way to do what I want is to simply install Windows 7 and, during the install process, select my current Ubuntu ext3 partition as the Windows 7 system partition. The suggestion said the Windows 7 install process would overwrite the MBR with the Windows boot loader, effectively “uninstalling” GRUB 2. The Windows boot loader will “find” the existing XP installation and give me a choice between Windows 7 and XP at boot time.
   
  Does that scenario sound right? Would it work the way I have described it? (I know I would no longer have Ubuntu. That is OK; I intend to reinstall it later.)
   
  For what it is worth, here is my current partition layout:
   
  /dev/hda - 320 GiB internal hard drive
       /dev/hda1 - 37.26 GiB ntfs boot (Windows XP)
       /dev/hda2 - 18.63 GiB ext3 (Ubuntu 9.10 /root)
       /dev/hda3 - 1.69 GiB linux-swap
       /dev/hda4 - 240.51 GiB extended
            7.84 MiB unallocated
            /dev/hda5 - 210.49 GiB ntfs (Windows XP “data”)
            /dev/hda6 - 30.01 GiB unknown (TrueCrypt encrypted device “unknown” to GParted)

---

### Post by cbecker78 on 2010-06-10
It worked fine when I tried windows 7 alongside xp.  I did not have ubuntu on that pc, but if you reformat the partition that ubuntu and grub are sitting on, you should be fine.

---

### Post by ba_saish on 2010-06-11
I think it should work fine, as you are over writing the GRUB, and no longer want ubuntu, it should not be any problem.

---

### Post by Mark Phelps on 2010-06-11
> **roddhall said:**
> I have my system set up to dual boot Ubuntu 9.10 Karmic Koala and Windows XP Pro, using GRUB 2 (1.97~beta4) as the boot loader. I want to remove Ubuntu and GRUB 2 from the system and install Windows 7 in a dual boot environment with Windows XP. My concern is to be sure that in the process of removing Ubuntu I do not make my system unbootable by removing or otherwise screwing up GRUB without replacing it with the Windows boot loader.
You will have no choice in the matter -- MS Windows OS installs ALWAYS overwrite the MBR, without asking.  This will effective remove GRUB from your MBR (in a single-drive system).
   
> I read a suggestion saying that the most straightforward way to do what I want is to simply install Windows 7 and, during the install process, select my current Ubuntu ext3 partition as the Windows 7 system partition. 
Haven't actually tried it your way, but my guess is that since Win7 can't read Linux-formatted partitions, it won't even "see" the Ext3 partition.  Safer approach would be to boot from a GParted LiveCD first, remove the Ext3 partition, and leave it as unallocated space.  Win7 will see that.

> The suggestion said the Windows 7 install process would overwrite the MBR with the Windows boot loader, effectively “uninstalling” GRUB 2. The Windows boot loader will “find” the existing XP installation and give me a choice between Windows 7 and XP at boot time.
See my first comment, and yes, it will create an OS selection menu that will include XP -- but it will not call it "XP".
   
BTW, you will need to install Win7 in a Primary partition -- which it will create automatically if you select the unallocated space.

---

### Post by X-Windows on 2010-06-11
You shouldn't have any trouble. Windows is very good at annihilating every operating system it sees.

---

