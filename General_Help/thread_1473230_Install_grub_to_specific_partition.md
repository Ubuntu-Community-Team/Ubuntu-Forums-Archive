---
title: "Install grub to specific partition"
date: 2010-05-05
forum: General Help
---

### Post by sabrehagen on 2010-05-05
On my netbook I have many partition for many different operating systems. I have Windows 7 on partition 2, and Ubuntu on partiton 3. Previously I could use GParted to set the boot flag for the drive to whichever partition I desired. If I set it to partition 2, I got the Windows bootloader, and if I set it to partition 3, I got the Ubuntu bootloader. Now if I set the boot flag to my Ubuntu partition, I get a message something along the lines of "disk not found". I can't recall its exact message at the moment. When setting up Ubuntu the installer has the "Advanced" button on the last page which gives you the option of which partition to install Grub to. Is there any way I can access this again, or a utility that will do the same thing? I have used the grub program in the following way to restore the Ubuntu bootloader

sudo grub
root (hd0,0)
setup (hd0)

but the boot flag is still on my Windows partition, suggesting Grub has overwritten Windows' bootloader. How can I tell grub which partition to install to?

I'm using 10.04 and Grub2.

Cheers!

---

### Post by nitstorm on 2010-05-05
Maybe this could help??
[HTML]http://ubuntuforums.org/showthread.php?t=1345191[/HTML]ubuntuforums.orgubuntuforums.org/newreply.php

---

### Post by wilee-nilee on 2010-05-05
> **nitstorm said:**
> Maybe this could help??
[HTML]http://ubuntuforums.org/showthread.php?t=1345191[/HTML]ubuntuforums.orgubuntuforums.org/newreply.php

I don't think easybcd will read ext4, that link is for previous extentions.

@thread starter what do you think about having grub installed correctly and having a choice at boot to any of the operating systems. The way you have gone about is why your where your at. If you would like to have grub show all of the OS, post this bootscript. Just paste it to the thread highlight the whole text and click on the # in the top bar of the thread post gui,
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by toomuchcomputertime on 2011-02-07
EasyBCD works for me, I use it in Vista, and use it to boot puppy and Kubuntu.

---

