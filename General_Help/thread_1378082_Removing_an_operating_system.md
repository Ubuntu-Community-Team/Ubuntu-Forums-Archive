---
title: "Removing an operating system"
date: 2010-01-11
forum: General Help
---

### Post by ali999 on 2010-01-11
Hi,

I currently have a triple boot system setup using GRUB, with Ubuntu, windows vista and windows 7. All of these are installed in separate partitions. I want to now delete vista and format that partition. What would be the proper way to do this. When I load grub I am directed to a windows loader if i choose windows where i then pick between either vista or 7. Will formatting the partition remove this entry from windows bootloader? Will it change my partition names? Any help is appreciated.

---

### Post by zkriesse on 2010-01-11
Gparted..that's all I'm gonna say.... [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by bsh on 2010-01-11
just make sure grub is loading your xp partition's bootloader and NOT the one on the vista partition. if it's loading the vista loader and you format that partition, you won't be able to boot windows anymore (until you edit grub...)

---

### Post by ali999 on 2010-01-11
I know about gparted. Formatting the partition is not my problem. I am concerned about messing up the bootloader and nt be able to access anything after. How can I edit the windows bootloader settings? I installed 7  after vista so I figure the boot info is stored on that partition but how can I be sure?

---

### Post by oldfred on 2010-01-11
Windows 7 literally moves some of its boot files to the first install ( the one with a boot flag on). You will have to move the boot flag and run windows repair to reinstall the files that will be deleted. Then you will have to reinstall grub.

Vista (also 7) copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Vista or 7 repair
If rebuilding the BCD does not resolve the startup issue,
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Then with the win7 install dvd, used the repair command line and type:
bootrec /fixmbr (press enter)
bootrec /fixboot (press enter)
bootrec /rebuildbcd (press enter)

You will need to boot with your Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by ali999 on 2010-01-11
Thanks,

I'll try this tonight and let you guys know what happens

---

### Post by ali999 on 2010-01-11
I have a rather odd problem. Before I did anything I wanted to make a copy of my menu.lst file, but I can't find it anywhere. The file is not in /boot/grub/menu.lst like it always is. I even tried the following code to try and find the file ```
sudo updatedb && locate menu.lst
``` but all I got was 
```
/usr/share/doc/memtest86+/examples/grub-menu.lst
```
which is not the correct file at all. 

I am absolutely lost here, any help is greatly appreciated.

---

### Post by Gen2ly on 2010-01-11
Well, Ubuntu uses GRUB2 now so I'm guessing it's configuration location is different now.  Not using GRUB2 myself but backing it up should be necessary.  GRUB looks up the configuration file on disk when it boots so it shouldn't be a problem (unless you of course have to reinstall :D).  If I'm not mistaken, Ubuntu's GRUB device naming is still used in menu.lst equvilent so unless you change your partition order it shouldn't be a problem.  What partitions do you have Vista, 7, and Ubuntu on?

If you could afford it, hard drives are relatively cheap now days.  There's an CD called clonezilla that does a good job of cloning/backing up.  Anyways, something to think about :D.

---

### Post by oldfred on 2010-01-12
You did not say which version of Ubuntu you were using. If it is a new install of Karmic (not an upgrade) then you do have grub2 (1.97 beta4 currently).

Grub2 creates a new file grub.cfg that you do not edit but is created from other files every time update-grub is run, which now is more often.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

