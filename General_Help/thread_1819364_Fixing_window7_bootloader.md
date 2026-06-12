---
title: "Fixing window7 bootloader??"
date: 2011-08-06
forum: General Help
---

### Post by UltraNEO* on 2011-08-06
Hi there.. 

I seem to be having an issue with windows boot loader after reinstalling Ubuntu. Would be grateful if someone could help me.. Many thanks in advance! :D

Originally I left linux to install it's grub where-ever it wanted, now i discover it's on the windows drive :( Anyway since then the Linux drive failed and subsequently I've lost some data but I'll get over it!! On this replacement drive I've told Linux to use it's own drive for it's Grub.. created a 20Mb partition for boot. So now I need to sort out the windows drive but how? Can i repair this within Ubuntu, manually or do I just need to boot of the windows disk and tell it to repair itself?

---

### Post by ajgreeny on 2011-08-06
You may have made, and be using a separate /boot partition, but grub itself, as opposed to the grub configuration files is still on the windows7 disk, unless you set it to install on the second disk.

Somehow, you probably need to restore the windows mbr to your windows disk and put grub on to the ubuntu disk, then set the boot priority in your BIOS.  Putting grub on the ubuntu hard disk is easy to do with a ubuntu live CD, but the first I will have to leave to others to tell you, or for you to search for, but I am sure it is easy if you have a windows7 DVD, not a recovery DVD or recovery partition.

---

### Post by garvinrick4 on 2011-08-06
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by UltraNEO* on 2011-08-06
> **ajgreeny said:**
> You may have made, and be using a separate /boot partition, but grub itself, as opposed to the grub configuration files is still on the windows7 disk, unless you set it to install on the second disk.

Somehow, you probably need to restore the windows mbr to your windows disk and put grub on to the ubuntu disk, then set the boot priority in your BIOS.  Putting grub on the ubuntu hard disk is easy to do with a ubuntu live CD, but the first I will have to leave to others to tell you, or for you to search for, but I am sure it is easy if you have a windows7 DVD, not a recovery DVD or recovery partition.

Thanks. 

Grub is already on the second disk (intel ssd), it's also setup as the primary boot device in the bios so there's absolutely no reason for it to look elsewhere. The problem arises when I choose windows from the Grub menu... It'll try to load windows, eventually it''l just quit and return to loading Linux. lol  (My thinking was this... If i ever decide to ditch windows, Linux would continue to load without windows drive being present :/)

Even when set my windows (vertex2) as the primary boot device, I encounter nothing but the grub prompt. It seems for the time being, regardless of which for the time being I can only boot to Ubuntu - not such a bad thing but occasionally I like to play games.

By the way, I did try to fix windows, kinda expected Windows to replace grub with it's default loader 
instead, in return it give me the most unexpected error... Guess i assumed too much from microsoft!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=199336&stc=1&d=1312614001[/IMG]

---

### Post by UltraNEO* on 2011-08-06
> **garvinrick4 said:**
> [Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
 
Perfect!! 
Mucho appreciated. Windows seems to be booting!! :KS
 
Right, on to repairing the Grub... Oh i meant 'customizing' ;)

---

### Post by garvinrick4 on 2011-08-06
Windows 7 and Vista repair disks.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs](http://neosmart.net/blog/2009/windows-7-system-repair-discs)

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by UltraNEO* on 2011-08-06
Thanks again!! 
 
 
> **garvinrick4 said:**
> [HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
 
OK.. Before I preceed because I'm able to boot into Ubuntu, I'll assume i can fix/customize the working GRUB with some terminal commands or possible application? All I'd really like to do here is add additional boot options/paths for my windows drive. Perhaps in the long run it'll save me time accessing the BIOS everytime I want to play games?? Or is it best to leave GRUB at default and use the BIOS to switch boot drives??

---

### Post by garvinrick4 on 2011-08-06
> Or is it best to leave GRUB at default and use the BIOS to switch boot drives??Leave Windows drive be Windows grub cannot add any other operating systems only the
one Windows. With Ubuntu's drives grub2 it has a package called "os-prober" which go's out and fetches 
other operating systems and puts them in it as a menu entry at boot and its configuration file. When one opens a terminal and does an update of grub:
```
sudo update-grub
```So if Ubuntu's drive is set in BIOS first it will boot all operating systems when windows drive is booted first in order only windows will boot. Enjoy your UBuntu Linux, I believe you will make a fine Linux user. In upper right of Thread there is a Thread tools mark as Solved please, as you may help others solve same.

---

