---
title: "Grub (Hd0) Madness win xp vannished"
date: 2009-09-28
forum: General Help
---

### Post by Cjtouhey on 2009-09-28
Hey i recently installed Windows 7 on a partition as you do.

Reinstalled Grub, then modified the Menu.lst to add it to Grub Loader 

any ways when i installed Windows 7, Windows Xp Gamers edition ( a modded version of my win xp set up for optimal gamming) disapeared, any ways ive tried alot of variations of (Hd0,0) which goes into win 7 now used to go into xp (hd0,1) up to (hd0,3) all give me the error cant find BOOTMNGR or somthing.

any ways im kinda confused cause with the normal xp i just set it to the next HD0 number, win7 when i had it installed on other computer used to have its own bootloader could it be messing with my xp installation...??

ill leave a list below this of my partition sda1 ect if any one can help me find the right HD0 path

dev/sda1 ntfs : system reserved 
      /sda2 ntfs  win 7
     /sda3 ntfs  win xp
     /sda4 extened (linux ubuntu)
    /sda5 ext3
     /sda 6 linux swap







any ways if some one could tell me how to List my partitions in there (hd0,0) (hd0,1) names that would save me alot of time thanks all 

p.s dont know technichle name for HD0 mCJIGGYS :D

---

### Post by Darkwing-Duck on 2009-09-28
Here you go man. This will not only restore your MBR to reflect all 3 OS' but also allow GRUB to see and load each.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this can help ya!

---

### Post by Cjtouhey on 2009-09-28
Thanks for the sugestion but i dont need to reinstall grub i just need to find out why i cant boot my xp partition being that win 7 Ultimate takes up (Hd0,0) and ubuntu takes up (hd0,4) and win xp being sda3 should be one of the ones inbetween (hd0,0 and 4 but is not tis confusing??

---

### Post by oldfred on 2009-09-29
If you installed windows 7 after XP it moves the boot files to or from XP and creates a menu in the boot to choose which version of windows to boot. Or only one windows boot partition still works, but has the boot for both. Grub then cannot boot directly to the other windows partition.

If XP was installed second the drive the boot should be ok. But for it to work each of the windows boot still have to be in its own windows partition.

Partition numbering in GRUB starts at 0 where in Ubuntu it starts at a or 1. In fdisk - l it is sda1,sda2 etc, so sda1 = (hd0,0) in grub, sda2 = (hd0,1)
sdb1 will be (hd1,0).

If your enties are correct win7 is sda2 or (hd0,1) and XP is sda3 or (hd0,2) in Grub.

---

### Post by Cjtouhey on 2009-09-29
No ubuntu jaunty jackalop still counts from 0 in the HD0 , It seems that windows 7 and win xp are fighting for (HD0,0) , i uninstalled the vista boot loader and can get into xp but cant get into 7 now ive tried editing the boot loader for all sorts of variations but dosnt work

---

### Post by oldfred on 2009-09-29
Windows installs in the partition and that is why Grub works. I wonder if you used the Vista repair on win7 if it would put a boot into the partition for Grub to see? The boot partition supposedly was the same from Win98 thru XP, so are Vista and 7 the same?

If you want lots of info on what is in the MBR and partitions download this:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
creates results.txt in the same directory, post with code tags as it will be long.

---

