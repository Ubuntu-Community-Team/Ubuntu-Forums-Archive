---
title: "Windows 7 not booting after installing Ubuntu"
date: 2010-03-29
forum: General Help
---

### Post by Doctor Vapor on 2010-03-29
I just installed Ubuntu 9.10 Karmic to a computer where I also run Windows 7 64bit.  I resized my partician to 60GB to add Ubuntu.  After installing and updating, Ubantu works fine, however, when I try to boot Windows 7, it makes it to the “Starting Windows” screen and doesn't continue to boot.  It freezes and I can't access the OS.
 

 Has anyone else had this problem?  How can I fix this?

---

### Post by sky net on 2010-03-29
boot disc !!

---

### Post by oldfred on 2010-03-29
If you want us to review you system and see if we see something missing:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

You can use the windows CD/DVD to repair your windows install, but it may reinstall the windows boot loader into the MBR. Some repairs can be done from Ubuntu live CD or install.

Reinstall grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by nivetevin on 2010-11-07
wow...thanx..u really helped me..God bless You

---

### Post by Quackers on 2010-11-07
Please mark the thread as solved by using the Tread Tools near the top of the page.

---

