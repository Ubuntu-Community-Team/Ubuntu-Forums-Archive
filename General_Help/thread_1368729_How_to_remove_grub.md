---
title: "How to remove grub?"
date: 2009-12-31
forum: General Help
---

### Post by garfieldwasacat on 2009-12-31
Argh, I hope someone can help

I've un-installed Ubuntu Koala, as I wanted to do a fresh install

but when I reboot, grub is still somehow installed (but corrupt) and I cannot get into my Windows 7 partition

I tried to repair Win 7 via the cd but it cannot find problems

I've completely erased all partitions except Win 7 so there must be a grub folder there somewhere but I cannot see it?

Any ideas?

Thanks

---

### Post by lindsay7 on 2009-12-31
Grub changes the mbr for windows. How did you try to repair windows?

---

### Post by lisati on 2009-12-31
If you've deleted the Ubuntu partitions there won't be a grub folder in Windows unless you had a weird setup. To get rid of grub completely you need to boot from a Windows recovery disk and use the fixmbr command.

---

### Post by lindsay7 on 2009-12-31
Here is what you need to do,

To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:

   1. Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type Bootrec.exe, and then press ENTER.

Note To start the computer from the Windows Vista or Windows 7 DVD, the computer must be configured to start from the DVD drive. For more information about how to configure the computer to start from the DVD drive, see the documentation that is included with the computer or contact the computer manufacturer.
Back to the top
Bootrec.exe options
The Bootrec.exe tool supports the following options. Use the option that is appropriate for your situation.

Note If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you make sure that the BCD is completely rebuilt. To do this, type the following commands at the Windows RE command prompt:

    * bcdedit /export C:\BCD_Backup
    * c:
    * cd boot
    * attrib bcd -s -h -r
    * ren c:\boot\bcd bcd.old
    * bootrec /RebuildBcd

/FixMbr
The /FixMbr option writes a Windows 7 or Windows Vista-compatible MBR to the system partition. This option does not overwrite the existing partition table. Use this option when you must resolve MBR corruption issues, or when you have to remove non-standard code from the MBR.
/FixBoot
The /FixBoot option writes a new boot sector to the system partition by using a boot sector that is compatible with Windows Vista or Windows 7. Use this option if one of the following conditions is true:

    * The boot sector has been replaced with a non-standard Windows Vista or Windows 7 boot sector.
    * The boot sector is damaged.
    * An earlier Windows operating system has been installed after Windows Vista or Windows 7 was installed. In this scenario, the computer starts by using Windows NT Loader (NTLDR) instead of Windows Boot Manager (Bootmgr.exe).

/ScanOs
The /ScanOs option scans all disks for installations that are compatible with Windows Vista or Windows 7. Additionally, this option displays the entries that are currently not in the BCD store. Use this option when there are Windows Vista or Windows 7 installations that the Boot Manager menu does not list.
/RebuildBcd
The /RebuildBcd option scans all disks for installations that are compatible with Windows Vista or Windows 7. Additionally, this option lets you select the installations that you want to add to the BCD store. Use this option when you must completely rebuild the BCD.



USE the /FixMbr option.

---

### Post by garfieldwasacat on 2009-12-31
[LEFT][FONT=Lucida Console]Thanks for both of your replies!

[/FONT]```
BootRec.exe /fixmbr
```[FONT=Lucida Console]

did the trick[/FONT]
[/LEFT]

---

