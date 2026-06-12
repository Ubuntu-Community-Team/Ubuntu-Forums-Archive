---
title: "Booting Vista after installing Ubuntu 9.10"
date: 2009-11-28
forum: General Help
---

### Post by StuartN on 2009-11-28
***(I know this isn't a Windows 101 forum, but I am trying to migrate my grown-up baby to Ubuntu via a dual-boot with Vista, and have messed up the Vista, so any help appreciated).***

I have installed Ubuntu 9.10 on a Dell Inpsiron 1501 in order to dual boot with an existing Windows Vista. Ubuntu can access all the files on the Vista partition, but Vista does not boot (not that I care, but the owner of the laptop does).

The reason for the boot failure is that I deleted partition 1 (Dell diagnostics) and partition 2 (Dell recovery), then shrunk and moved Vista over to give me 20 GB for Linux. Obviously I deleted the MBR and the boot list on whichever partition was the boot partition - which would not be a problem in any other version of Windows because I could edit BOOT.INI, but not in Windows Vista.

Initially selecting Windows Vista in Grub caused a hardware restart. I used a Vista recovery disk in the hope that it would recreate Boot/BCD (the binary file replacing BOOT.INI). Now Vista makes an effort to boot, but I get errors like "RunDLL.exe not found", and an infinite disk-read. It seems to be reading the correct partition but something is missing.

Any ideas on how to repair the Vista boot process? (without destroying a completely functional Ubuntu).

---

### Post by hal10000 on 2009-11-28
You will either need a windows-PE CD (boot it and run bcdedit.exe from the command line) or a windows vista CD (boot it and run from the system recovery condole the program bootrec /fixmbr and/or bootrec /fixboot).

You will then get a new mbr from which you can boot windows, but your ubuntu cannot be booted anymore and you have to set up grub again (with your ubuntu live-cd) in order to boot both ubuntu and vista.

---

### Post by StuartN on 2009-11-28
> **hal10000 said:**
> You will either need a windows-PE CD (boot it and run bcdedit.exe from the command line) or a windows vista CD (boot it and run from the system recovery condole the program bootrec /fixmbr and/or bootrec /fixboot).

Many thanks, but the problem is slightly different - the Vista recovery option is allowing Windows to attempt to boot from the correct partition. It loads the splash screen and displays "Configuring Your Desktop" and then accesses the hard disk continuously.

I can CtrlAltDel to a Task Manager and start Explorer (as a non-administrator, temporary user - I cannot save settings), from which I see that the partition has been ennumerated as drive K:. There is no drive C:, E:, F:, G:, H:, I: or J:. D: is the CD ROM. There is no apparent file corruption when tested in Windows or in Ubuntu, and the system can be cleanly shut down. But I can not log in.

I assume that the Registry contains entries for system files on C:, and somehow needs to be reconfigured to ennumerate the Windows Vista partition as C: and not K:. I have followed the exact same procedure to dual-boot Ubuntu on the same model of laptop previously, except it was Windows XP and only required an edit of BOOT.INI.

How can I relabel the K: drive as C: at Windows bootup?

---

### Post by hal10000 on 2009-11-28
In the windows partitioning tool you have the choice to change the drive label, but i don't know if this is possible while the partition is in use.

I guess you can change it also in the windows registry. Maybe you should google for changing the drive label in windows registry.

---

### Post by StuartN on 2009-11-28
Hooray! I started in command line mode and ran BCDEDIT.EXE, and that was all that was required - I did not need to alter any configuration, merely to run this tool and it corrected the boot list to match the partitions.

*(I really, really hate Windows, these stupid binary configuration files and the registry - I would just nuke it on my own machine).*

---

