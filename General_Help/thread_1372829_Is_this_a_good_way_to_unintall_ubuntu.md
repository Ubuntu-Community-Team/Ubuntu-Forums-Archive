---
title: "Is this a good way to unintall ubuntu?"
date: 2010-01-05
forum: General Help
---

### Post by allmightymoo on 2010-01-05
Ok so making sure this is a safe thing to do in order to uninstall ubuntu...(dont worry i'm gonna reinstall it ;))

1. Repair windows startup using recovery disk i got from here >> [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

2. In windows use disk manager and delete the ubuntu partition

3. Thats all? everything is back to normal?

4. reinstall ubuntu
 
So is this a good way to uninstall ubuntu? Is there a better way? If you do have a better way i am new to ubuntu so be as clear as possible...pictures are helpful haha ;)

---

### Post by MelDJ on 2010-01-05
i think it would work.
if you have doubts try this: [http://www.techspot.com/vb/all/windows/t-38428-How-Do-I-Uninstall-Ubuntu-Linux-From-WinXP-Dual-Boot-Machine.html](http://www.techspot.com/vb/all/windows/t-38428-How-Do-I-Uninstall-Ubuntu-Linux-From-WinXP-Dual-Boot-Machine.html)

---

### Post by allmightymoo on 2010-01-05
ok so i tried it but the windows startup repair said that there were no problems...so maybe i should do that after i delete the ubuntu partition?

---

### Post by MichealH on 2010-01-05
Just Format or Delete the Ubuntu Parition but I wouldn't suggest Deleting it Just re-format it and Ubuntu is Uninstalled. I wont suggest doing it on the Windows Disk because you will be wasting your time with it formatting to NTFS hten you have to format it to ext etc.

---

### Post by allmightymoo on 2010-01-05
> **MichealH said:**
> Just Format or Delete the Ubuntu Parition but I wouldn't suggest Deleting it Just re-format it and Ubuntu is Uninstalled. I wont suggest doing it on the Windows Disk because you will be wasting your time with it formatting to NTFS hten you have to format it to ext etc.

Ok why does that waste time? just wondering...i dont know how to reformat it, i cant seem to do it in disk manager in windows. 

Also should i delete/reformat the linux-swap space too?

---

### Post by MichealH on 2010-01-05
Nope don't delete the swap if you dont want to. I was just saying that I you used the windows disk manager it would of formatted to NTFS and basically wasting time.

---

### Post by Elfy on 2010-01-05
I would use a partition editor to remove the linux partitions - including swap - there's one on the livecd - System Admin - Partition Editior.

Once that's done fix the windows boot.

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

---

### Post by prshah on 2010-01-05
> **MichealH said:**
> Just Format or Delete the Ubuntu Parition but I wouldn't suggest Deleting it Just re-format it and Ubuntu is Uninstalled. 

If you have GRUB installed and you do this, neither operating system will boot. 

> **allmightymoo said:**
> Also should i delete/reformat the linux-swap space too?

It is optional; you can reuse it when you install a fresh Linux, or you can delete it, resize it, whatever. It's a choice, not a requirement.


To "properly" remove GRUB and replace with Windows bootloader so that your Windows will boot correctly, you need to use the "Recovery Console" that is available only off your original bootable XP CD.

Boot off the CD, and choose "R" to start "Recovery Console" when prompted. This will be on the VERY FIRST SCREEN after basic loading of Windows files, and if it is not there, then your CD is either not the same version as your XP installed, or some other problem.

In the recovery console, you can use the following commands```
FIXBOOT C:
FIXMBR
BOOTCFG /rebuild
```

The first two commands will restore the Windows bootloader and check / replace files required to boot Windows. The last command will "add" your existing Windows installation to the list of available operating systems; this last command is optional, but safer to do.

Note: Windows XP is very sensitive as far as the booting process goes, so you perform this at your own risk.

After removing GRUB and successfully booting into Windows, you can delete the Ubuntu/swap partitions if you want to do so.

---

### Post by allmightymoo on 2010-01-05
ok well i have win7 not XP. i have win7 recovery disc that i got from here>> [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/) so will that work?

OK...i saw this on a video...will this work? if not if you could explain another soultion step by step i would greatly appreciate it :)

1. Start up Windows 7
2. Click start, then Control Panel
3. Search for "partition" in Control Panel
4. Click create and format hard disc partitions
5. Locate the partition you created for Ubuntu, right click it then click 'Delete volume' and press yes
6. Ubuntu is now removed but you are left with the GRUB loader which will not allow you to access Windows
7. Insert your Win7 recovery disk
10. Select Win7
11. Click Command Prompt
12. In command prompt type 'Bootrec.exe /FixMbr' and press enter
13. Shutdown your computer & remove the install disc
14. Ubuntu is now removed along with GRUB loader, you are left with Win7.

This video i got this from said it was originally for win vista but would work w/ win 7. Here's the video>> [http://www.youtube.com/watch?v=4nqvCQd3bLI](http://www.youtube.com/watch?v=4nqvCQd3bLI)

Thanks for the help!

---

### Post by prshah on 2010-01-05
> **allmightymoo said:**
> 
12. In command prompt type 'Bootrec.exe /FixMbr' and press enter

Seems OK to me. If you are doing a fresh install of Win7 then GRUB will get overwritten anyway, and these steps are not required.

My previous post assumed that you have an existing installation of Windows which you don't want to lose.

---

### Post by L4U on 2010-01-05
Here's how I installed a newer version over the previous version:

After inserting Live CD and preparing to install:

1. Prepare Disc Space > Specify partitions manually > Forward
2. Select old Ubuntu partition > Change
3. Edit Partition > Use as: > Ext3 or Ext4 > select "Format the partition:" box > Mount point: > "/" > OK > Forward

---

