---
title: "Win7 nuked, looking at using ms-sys"
date: 2010-10-18
forum: General Help
---

### Post by snarab2010 on 2010-10-18
Hello everyone, I'm brand new here, and I'd like to ask the experts a question.

You see, I have a system that has openSUSE 11.2, Windows 7, and Windows XP installed on separate partitions, and I have Ubuntu 10 installed via wubi into my Windows XP. I tried to install a custom patch to Windows 7 and now it won't boot up! All I get is the underscore blinking at me from the top left corner! I can get into my other operating systems just fine, though.

I was looking at this package to help me out:
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

I don't really care if I end up with GRUB or mbr as my bootloader, I just want to be able to get into all of my operating systems. Any advice would be deeply appreciated.

Thanks in advance!

---

### Post by 3Miro on 2010-10-18
If you cannot  get into Windows 7, this is probably because of a windows 7 specific problem. Since the problem occured right after a windows upgrade and only windows is affected, it will not be a Linux issue. Grub can easily boot all of the systems, there is no need for another program. Basically, this program will probably not fix your problem.

---

### Post by oldfred on 2010-10-19
per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Otherwise you can use a windows repair cd and run fixmbr or BootRec.exe /fixmbr  depending on version of windows.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by snarab2010 on 2010-10-19
Thanks for the advice, guys.

The only issue I really have against /fixmbr is that I have been told that it may not see all of my operating systems after it's finished. I'd like to minimize the likelihood of this happening, but if you all recommend that it is safe enough, then I'll give it a try.

Would running bootrec.exe /ScanOs help in any way?

---

### Post by oldfred on 2010-10-19
Windows only finds windows systems and moves all the boot files from other systems into the one windows primary partition with the boot flag (active partition).

If you want to boot Ubuntu or other systems, you need to use grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

