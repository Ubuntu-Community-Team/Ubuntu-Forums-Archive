---
title: "Weird dual booting problem"
date: 2010-03-13
forum: General Help
---

### Post by Tango91 on 2010-03-13
Hi all,

I dualboot XP 64-bit and Ubuntu 9.10 on my comp and i have a strange (and frustrating problem with booting. 

(sorry, this is going to be a bit of a novel)

Up until yesterday all was well, i could boot into either as i pleased and life was great.
Then, out of the blue, windows decided that it couldn't find NTOSKRNL.dll (which it does at least biannually :p ).

"oh, god" i thought. "this means a complete reinstall of windows (the XP64 disk i have doesn't have a recovery console option, and i have no floppy drive.)

I decided to boot with the windows cd in the drive, and went into the setup utility. no option for a recovery console was displayed, so i quit outand rebooted. I did this with several XP disks we have about the place, including a dedicated recovery console disk (although this doesn't contain the .cab files i'd need to extract into system32.

In a nutshell, i did nothing, i committed no actions nor installed anything at all.

I restarted my computer without a cd in the drive, just to try it... and i got booted straight into windows, with no problems. (this amazed me, i hadn't done anything and this error is usually so persistent).

Just one problem was obvious: no GRUB menu on booting.

I booted off my Ubuntu livecd and went to the console.

previously, in other versions of linux i have fixed this by issuing the command 'sudo grub' then 'root (hd0,0)', 'setup (hd0,0)' and 'exit'

This time, it gave me the error: 'no GRUB installed'.

i've looked in /boot/grub/ and there is no menu.lst file. the rest of the files are there, but not that one.

I tried 'sudo grub-install' in the cosole and it goes through the motionsof grinding and whirring and then declares that it can't be done.

The 'install Ubuntu to hard drive' app cannot see any operating systems on there at all, but GParted shows all my partitions, which i will list for your reference:

hda0: ~20GB ext4, this is (was) root
hda1; ~30gb ext4, this is /home
hda2: 2GB swap
hda3: 100GB ntfs, windows on here.

hdb: 80GB storage drive, not used for operating systems.


If i use GParted to change the flags so that hda0 has the boot flag instead of hda3 then the computer can't find an operating system when it boots.


i've searched around a lot and i can't find any method that helps me get GRUB back except reinstalling Ubuntu, which i don't want to resort to yet.

help me, ubuntu forums, you're my only hope. [-o<

Thanks in advance, TJ

---

### Post by oldfred on 2010-03-13
If you installed Karmic clean and not an upgrade from 9.04 you have grub2 which is installed differently.

The boot flag must be on the windows partition that is used to boot. Linux does not use it, but some BIOS need a boot flag on the drive.

If in what you have done has installed grub legacy it confuses things and needs to be deleted to get grub2 to work.

If all you have to do is install grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you need more help just ask.

---

### Post by Tango91 on 2010-03-14
Thanks for your help,i'll try that in a bit :)

---

### Post by Tango91 on 2010-03-14
Thank you so much oldfred :) worked like a charm :D
 
i guess i have a lot more to learn about Ubuntu... :redface:

---

