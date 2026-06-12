---
title: "Complete screw up regarding grub/Windows MBR"
date: 2010-06-16
forum: General Help
---

### Post by sage_viper on 2010-06-16
Okay, so I decided that I no longer wanted to dualboot Windows with Ubuntu, so I went into Windows and blatantly deleted the Ubuntu partition. Now, I was booting with Grub, mind you, and now my computer can't boot into any OS because it can't find Grub. How can I get my computer to go back to reading the Windows MBR instead of grub?

At least I think thats what is happening...

---

### Post by oldfred on 2010-06-17
You can use a windows repair CD and run fixMBR to update MBR with a windows boot loader.

Or from Ubuntu and lilo is often on many repair CDs.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by sage_viper on 2010-06-17
what repair disk? An Ubuntu live disk? Just tried that, didn't work. It said that it was missing some archives and couldn't install, and then wouldn't run the 
sudo lili -M /dev/sda mbr
command.

How would I do it with a Windows disk? Its Windows 7, by the way. I guess fixMBR doesn't work with Win7. I tried to use the other way I found online, but that didn't work either.

---

### Post by proggy on 2010-06-17
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by wojox on 2010-06-17
You need your Windows 7 Disk [How to repair MBR on Windows 7]("http://www.ehow.com/how_4836283_repair-mbr-windows.html")

---

### Post by sage_viper on 2010-06-17
> **wojox said:**
> You need your Windows 7 Disk [How to repair MBR on Windows 7]("http://www.ehow.com/how_4836283_repair-mbr-windows.html")
I've tried that, its an awful tutorial =/

But I'll try that repair disk, thanks for the link, proggy.

---

### Post by wilee-nilee on 2010-06-17
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is the whole command set I have highlighted what oldfred is referencing, and this list is courtesy of him as well. If you look at the http it is a tutaorial which shows the process of getting to the command line in W7 recovery.

I didn't look at wojox link but I don't have to they know the drill.;) I'm sure it's correct in other words.

---

### Post by sage_viper on 2010-06-17
> **wilee-nilee said:**
> 1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is the whole command set I have highlighted what oldfred is referencing, and this list is courtesy of him as well. If you look at the http it is a tutaorial which shows the process of getting to the command line in W7 recovery.

I didn't look at wojox link but I don't have to they know the drill.;) I'm sure it's correct in other words.
Much appreciated! That worked! Got scared there for a second, hah.

Thank you all for your replies and help! Thats definitely a mistake I won't make again.

---

### Post by wilee-nilee on 2010-06-17
> **sage_viper said:**
> Much appreciated! That worked! Got scared there for a second, hah.

Thank you all for your replies and help! Thats definitely a mistake I won't make again.

He he I bet you never remove a OS without having the boot under control again.;)

---

