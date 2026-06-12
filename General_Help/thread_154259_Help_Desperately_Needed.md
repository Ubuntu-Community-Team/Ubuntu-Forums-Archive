---
title: "Help Desperately Needed"
date: 2006-04-02
forum: General Help
---

### Post by new2linux2009 on 2006-04-02
i tried to install ubuntu when after partitioning with Partition Magic the hdd i can't start windows.  It now says that a problem had been detected and Windows has been shut down to prevent damage to your computer.  If the is the first time you've seen this Stop error screen...the error number is Stop: 0X00000024 (00190203, 0x81AD1848, 0xC0000102, 0X000000).  I just want windows to work again and don't have a windows xp cd.  PLEASE HELP ME I AM SOOOO DESPERATE.  If the is ABSOLUTELY NOTHING that can get windows back to normal the how do i install ubuntu over it....please give me the full instructions I am new to linux.  I just don't know what to do.....](*,)

---

### Post by dcstar on 2006-04-02
[QUOTE=new2linux2009]i tried to install ubuntu when after partitioning with Partition Magic the hdd i can't start windows.  It now says that a problem had been detected and Windows has been shut down to prevent damage to your computer.  If the is the first time you've seen this Stop error screen...the error number is Stop: 0X00000024 (00190203, 0x81AD1848, 0xC0000102, 0X000000).  I just want windows to work again and don't have a windows xp cd.  PLEASE HELP ME I AM SOOOO DESPERATE.  If the is ABSOLUTELY NOTHING that can get windows back to normal the how do i install ubuntu over it....please give me the full instructions I am new to linux.  I just don't know what to do.....](*,)[/QUOTE]
You have a Windows problem, not a Linux one. I suggest you post in a Windows forum for assistance on trying to restore it.

If you want to install Linux over it, got to the Ubuntu home page and follow the instructions there and you should be fine.

---

### Post by r4ik on 2006-04-02
First you have to go borrow a xp disk.
Everything mentioned below should go for xp also, after some research you can use the NT4 Workstation floppy it can be found here  [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Using Recovery Console on a Single Drive Computer
If your computer contains only a single NTFS volume and no additional Windows 2000-based computers or hard disks are available to use for the previously described methods, you can boot from the four Setup disks to run the Chkdsk tool with the Ntfs.sys driver disabled. To repair a NTFS volume by using Recovery Console, use the following steps:
1.	Start the computer by using a Microsoft Windows 95/98 startup disk with CD-ROM support (or from another computer with a CD-ROM drive, insert the Windows 2000 installation CD-ROM).
2.	Change to the CD_ROM:\Support\Bootdisk folder, and then run Makeboot.exe or Makebt32.exe to create the four Windows 2000 Setup disks.
3.	Using Notepad, modify the Txtsetup.sif file on the first Setup disk you created in step 2:
a. 	In the [FileSystems.Load] section, locate the line that begins with "ntfs."
b. 	Insert a semicolon ; at the beginning of the line, as shown in the following example:

[FileSystems.Load]
fat      = fastfat.sys
;ntfs     = ntfs.sys 

c. 	Save your changes.
4.	Start the computer that is experiencing the "stop 0x24" error message by using the four Setup disks. When the Welcome to Setup dialog box is displayed, press F10 to start Recovery Console.
5.	Run the following command to repair the corrupted NTFS partition:
chkdsk driveletter: /p
6.	Type exit to quit Recovery Console, and then restart the computer.

Sorry for the multiple edeting hope it helps.

---

### Post by marcykid on 2008-02-13
This happened to me too on my Toshiba  laptop running XP.  Ubuntu corrupted the windows ntfs boot ini.  Blue screened immediately after install with a Stop 0x24 error.  I installed Ubuntu using the Wubi installer, exactly as described on their website.  Recovery using boot disks aside, what's actually going on here?  My xp hasn't crashed in... um, well... never (until now).  Clearly Ubuntu and/or its installer have sufficient access to the Win boot ini in order to punk it.  Anyway, currently neither os will boot.  They're both fuggin' dead.

---

