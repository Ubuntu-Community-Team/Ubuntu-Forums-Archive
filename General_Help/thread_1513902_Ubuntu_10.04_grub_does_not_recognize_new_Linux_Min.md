---
title: "Ubuntu 10.04 grub does not recognize new Linux Mint installation. Please help! :("
date: 2010-06-20
forum: General Help
---

### Post by KarenM on 2010-06-20
Hi,I have a multiboot system with Ubuntu Lucid and Windows 7. Today I installed Linux Mint 9 for testing in another partition. I was expecting Mint to overtake the grub loader with its own,but unfortunately that didnt happen. Instead, I was taken to the Ubuntu grub loader after rebooting. And as I was expecting,there was no sign of Linux Mint in the list. 

I know both the distros use grub2, and there might be a conflict between the two with controlling the bootloader. But, I want to keep both the distros. :( So is there some way this problem can be rectified? If nothing else, can I add Mint to Ubuntu's grub loader somehow? 

Please help me! :(

Thanks in advance!

-Karen :)

---

### Post by NCLI on 2010-06-20
Boot into Ubuntu, then open a terminal and run this:
```
gksudo update-grub
```
Then reboot. Mint should show up now, if it has been properly installed.

---

### Post by Rubi1200 on 2010-06-20
> **NCLI said:**
> Boot into Ubuntu, then open a terminal and run this:
```
gksudo update-grub
```Then reboot. Mint should show up now, if it has been properly installed.

If I am not mistaken the command is

> sudo update-grubAlso, if this does not work you will have to re-install GRUB2 to the MBR using the LiveCD.

Instructions here:

[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling%20from%20LiveCD")

Can you still access Windows when you boot? If so, my advice may not be correct to reinstall GRUB, as now I am unsure as to why Windows might show up but not Mint.

---

### Post by KarenM on 2010-06-20
Thank you so much, NCLI and Rubi1200 !! :D 

gksudo update-grub This worked!! :D Now Mint is added to the Ubuntu grub loader. 


Just one more thing! Is there some way i can have Mint's boot up screen  (the screen with the progress bar) back? Unlike when i just had Mint,  now I see the text based boot up process, and I think, it takes slightly  longer to boot than it did with the progress bar screen. Maybe I'm  wrong about the boot up time, but I prefer the progress bar screen. :P  So Is there someway to have the mint splash screen back? Since Mint is  based on Ubuntu, I guess, the process to enable/disable the splash  screen should be similar(?).

TIA,
Karen :)

---

