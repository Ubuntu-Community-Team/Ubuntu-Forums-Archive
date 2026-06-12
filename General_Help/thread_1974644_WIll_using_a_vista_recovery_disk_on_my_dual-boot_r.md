---
title: "WIll using a vista recovery disk on my dual-boot remove grub?"
date: 2012-05-06
forum: General Help
---

### Post by syerra on 2012-05-06
Yep, pretty much as I said in the title. I don't want to remove grub with 12.04 which has become my principal OS and my vista is way beyond corrupted. I need to use the Vista recovery disks and now wonder whether it'll affect the MBR.

Any tips would be appreciated, thanks.

---

### Post by Cheesemill on 2012-05-06
It may do more than remove grub. Depending on the recovery disks it might wipe all traces of Ubuntu from your computer and return it to the state it was in when purchased.

Make sure you have a full backup before proceeding any further.

---

### Post by syerra on 2012-05-06
Yes cheesemill, but I'm not talking about re-installing and formatting my hard drive, just repairing the install I have. Will that format the MBR or not is the question...

---

### Post by Cheesemill on 2012-05-06
Sorry, thought you were reinstalling Windows.

Anyway the answer is yes, fixing Windows with a recovery disk will restore the Windows MBR leaving you unable to boot into Ubuntu.
See here for how to restore grub:
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by oldfred on 2012-05-06
If you run the automatic repair 3 times, then one of those overwrites the MBR. But you can use the Windows command line. (Windows has command line?)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #[COLOR=DarkRed]updates MBR master boot record  do not run if you still want grub[/COLOR]
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

