---
title: "Serious Grub problems need help"
date: 2010-06-11
forum: General Help
---

### Post by rasmus91 on 2010-06-11
Hi there

I just aquired an acer aspire 5745G today.

I was overall very happy with the purchase, but right now i frustrated to tears!

When you first boot up this computer it needs you to configure windows 7. There is no Windows 7 Disk with the computer. When the computer is booted it asks you to make a recovery copy. This requires 3 DVDs, somethingh i happen not to be the owner of. After configuring windows i installed ubuntu for dualbooting, then i went on to use windows.

I started Installing a program for windows called Daemon Tools , and this asked me to restart the computer halfway through the installation. now, when the computer restarted i got the post screen, and then a black screen with a white "Dos-like" cursor in the upper left corner.

I never get to see Grub. I happen to suspect that this ruined Grub, and so i need someone to tell me how to restore Grub. And just to be sure you get me right it's GRUB2 (im using Ubuntu Lucid Lynx) And doing: ```
sudo grub
``` tells me: Command not found.

i haven't been able to find a good guide on how to do this, and i need help right now. I need to make Grub work so i can boot both Ubuntu And Windows 7. If I just erase Ubuntu and then reinstalls it, will it do the trick? (also make me able to boot windows?)

Help will be greatly appriciated. Thanks 

Doing a clean reboot will be sufficient for me as i can easily reinstall Linux

Rasmus

---

### Post by oldfred on 2010-06-11
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

You really should create the windows DVDs. Sometimes mistakes are made and you need to repair them.

---

### Post by rasmus91 on 2010-06-11
> You really should create the windows DVDs. Sometimes mistakes are made and you need to repair them.

I know and believe me, that's my top priority.

How ever; Theres one strange thing. Everytime i restart my computer after windows has updated i can not boot (windows nor Linux), But if i then format the ubuntu partition and then reinstalls ubuntu i can boot just fine again. Im guessing windows 7 updates are messing with Grub, but how can i make sure both keeps being bootable?

---

### Post by X-Windows on 2010-06-11
If you have the Windows 7 install discs and are fine with reinstalling both windows and ubuntu, I wrote a how-to that may help you. [http://ubuntuforums.org/showthread.php?p=9343022](http://ubuntuforums.org/showthread.php?p=9343022)

That method gives you Windows 7 in its own compartment, a shared partition between them and Ubuntu's nifty boot loader. Works like a charm and only takes ~1.5 hrs to do a total install.

---

### Post by rasmus91 on 2010-06-11
> If you have the Windows 7 install discs and are fine with reinstalling both windows and ubuntu, I wrote a how-to that may help you. 

mhm, Sounds lovely, but I am very (truly) sorry to say that the computer didn't come with such disks :(

How ever, do you know how to make sure Windows 7 doesn't ruin the bootloader? (just did it again, and i have to reinstall ubuntu afterwards each time to reinstall Grub :( )

---

### Post by Jahocolips on 2010-06-11
[http://ubuntuforums.org/showthread.php?t=1505818](http://ubuntuforums.org/showthread.php?t=1505818)

---

### Post by X-Windows on 2010-06-11
Due to my lack of 75 posts to pm I'll post here then edit to remove in an hour.

If you need a copy of Windows 7 I'd be glad to send you mine, it's around 4Gb if you are on dial-up. You should have gotten a cd when you purchased your comp anyway.

---

### Post by mr clark25 on 2010-06-11
if you dont want to reinstall ubuntu every time, you can restore grub with a live cd.

run these commands in a terminal (replacing sda5 with your linux partition):
```

sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda5 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit

```

"grub-install --recheck /dev/sda" may install grub legacy. but, it may also install grub2. anyone know if that installes grub legacy or grub2?

---

### Post by tomillares on 2010-06-11
I had a netbook samsung, and in the boot it had a function to recovery the computer to the original state. I had to press F2 (or maybe F4 or F8. I don't know if the acer aspire 5745G has something similar.

---

### Post by oldfred on 2010-06-11
You can download a repair disk.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Windows has software that writes into the MBR which is supposed to be just for booting.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by rasmus91 on 2010-06-11
> Due to my lack of 75 posts to pm I'll post here then edit to remove in an hour.

Sorry, It seems to work now, Even though the solution seemed to have nothing to do with the problem.

But, thanks for all your nice responses, i'll be sure to save them for later use! :) you guys are the best, in case you didn't already know.

Just two questions: >  	
if you dont want to reinstall ubuntu every time, you can restore grub with a live cd.

run these commands in a terminal (replacing sda5 with your linux partition):
Does this require internet?

And

> "grub-install --recheck /dev/sda" may install grub legacy. but, it may also install grub2. anyone know if that installes grub legacy or grub2? 

does it matter?

One last thing though:> Windows has software that writes into the MBR which is supposed to be just for booting.

i will just have a look at this ;)

Again, thanks everyone!

UPDATE: as [this site]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR") suggests i have McAfee installed, and it could very well be related to the problems, I think i will uninstall McAfee now, just to see what happens, and also because i dont care for McAfee.

(thanks to Oldfred for providing links)

---

