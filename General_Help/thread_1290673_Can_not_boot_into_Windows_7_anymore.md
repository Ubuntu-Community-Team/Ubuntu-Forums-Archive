---
title: "Can not boot into Windows 7 anymore"
date: 2009-10-13
forum: General Help
---

### Post by tab1293 on 2009-10-13
Hi, the other day I tried installing karmic koala beta. I have two HDDs in my computer, a 500GB with Windows 7 on it and an empty 250GB which I was installing Ubuntu on. When going through the Ubuntu installation a strange thing was evident in the partition manager, Windows was said to be found on the 250GB hdd instead of the 500. I think ubuntu thought this because windows' boot loader was on the mbr of the the 250gb hdd. I proceeded to install and once done grub loaded but no option to boot into windows came up. I tried directly booting from the 500gb hdd in my bios but it gave me an error. Now I installed jaunty and the problem still exists. My plan to fix this is to try to erase the mbr of the 500gb hdd and use grub to boot into windows 7. Can anybody tell me how to do this?

Note: I already tried to fix windows 7 bootloader following this guide [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

I got errors in each method.

---

### Post by quixote on 2009-10-14
What happened is that grub wrote over the Win7 MBR, since that was on the drive where you put Ubuntu.

This was easy to fix in WinXP and earlier.  [COLOR="Red"][Edit: Nope.  This doesn't work any more.  See next comment.][/COLOR]  I don't know if Win7 works the same way, but I'd bet it does.  In the Good Old Days you would  

1) use any Windows or even DOS bootable medium (Bootable CD, floppy, USB, whatever).
2) boot into recovery mode.
3) once you have the command line prompt, type "fixmbr" (no quotes)
I'm not sure if there would be an issue with it trying to work on the wrong drive.  I don't think so, but if you can, it might be good to disconnect the 250GB drive.

That makes Windows bootable again.

For grub to see both OSes, you just need to make sure the Windows entry points to the right drive and partition.  If you need them, there are good instructions here:  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  That's for grub2, which is what karmic uses, I think.  The old instructions are here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by PrePenguin on 2009-10-14
Change in Bios to boot to windows 7 HD and let it boot then use easyBCD tou manipulate the MBR because Vista and windows 7 no longer use the boot.ini manipulation for Booting. There mayb e otherways if you choose but this is the easiest for me.

---

### Post by quixote on 2009-10-15
hah.  I had a sneaking suspicion the old method might not work any more.  Good to know how to do it.  Even though, if I'm lucky, I won't have Windows on a computer in this world or the next :D .

---

