---
title: "Grub doesn't load Win7"
date: 2012-09-09
forum: General Help
---

### Post by someone307 on 2012-09-09
Hello!

I've installed Ubuntu 12.04 today on the same drive as Windows 7(I used option "Install Ubuntu alongside them").

My laptop is Acer M3 with two drives: one 500gb HDD and 20GB SSD which was used for hibernation file by default factory set-up.

Ubuntu works properly. I can start Acer Windows restore utility as well as. Also there is another default Windows restore  utility in the list which appeared after I used "Boot Repair utility". I get the following message when I try to boot with this option:  "0x00000007 The boot selection failed because a required device is inacessible." 
As for Windows itself, it just don't boot up. I have black screen for few seconds and then reboot. 

I tried to use Boot Repair utility and still have the problem. Here are results from previous actions with it:
[http://paste.ubuntu.com/1195167](http://paste.ubuntu.com/1195167)
[http://paste.ubuntu.com/1195178](http://paste.ubuntu.com/1195178)
[http://paste.ubuntu.com/1195231](http://paste.ubuntu.com/1195231)
[http://paste.ubuntu.com/1195297/](http://paste.ubuntu.com/1195297/)

---

### Post by sienile on 2012-09-09
Have you tried```
sudo update-grub
```?

---

### Post by someone307 on 2012-09-09
Yes. Nothing changes.
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
done


---

### Post by sienile on 2012-09-09
Have you tried booting from the 2 Windows Recovery entries? It seems odd that you would have 2 of them.

---

### Post by sienile on 2012-09-09
I just noticed something fishy in your Boot-Info:
> Disk /dev/sdb: 20.0 GB, 20014718976 bytes
255 heads, 63 sectors/track, 2433 cylinders, total 39091248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048     8,390,655     8,388,608  84 OS/2 hidden C: drive
/dev/sdb2           8,392,704    39,086,079    30,693,376  73 Unknown

It seems you have a 2nd HDD with a OS/2 partition... Maybe this is Windows acting weird? Someone with more knowledge on boot errors will need to help you. This is way out of my league.

---

### Post by oldfred on 2012-09-09
Windows NTFS partitions have to have a NTFS boot sector (PBR). You have grub2's boot loader installed when it need code to boot with bootmgr in that space.

```
sda2: ____________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
[COLOR=Red]    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 930810776 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.[/COLOR]
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

```

Testdisk can restore the backup if you only wrote grub once to the partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by someone307 on 2012-09-10
I decided to repair the boot sector from Ubuntu, but I'm stuck on the 6th step. There is no "
BackupBS" :(
[IMG]http://i.imm.io/DQsN.png[/IMG]

Can I rebuild boot sector without loss of files?

---

### Post by oldfred on 2012-09-10
Run the Rebuild BS to create a new NTFS boot sector. As long as grub is in boot sector Windows will not even see it. But I think Testdisk only creates a XP type NTFS boot sector. The Windows 7 one is different as it has bootmgr to boot instead of ntldr. But Windows repairs should then work.

From Windows 7 run chkdsk. I have XP and used a Windows 7 repairUSB to run chkdsk on my XP partition. It converted it to a Windows 7 boot sector.

If chkdsk does not convert it you can run these from Windows 7 also.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by someone307 on 2012-09-10
Thank you very much! Hope this will help.

---

### Post by someone307 on 2012-09-10
Thank you again! I'm writing from Windows 7, bootrec.exe was the solution! :)

---

### Post by someone307 on 2012-09-10
Solved!

---

