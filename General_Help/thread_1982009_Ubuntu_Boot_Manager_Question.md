---
title: "Ubuntu Boot Manager Question"
date: 2012-05-17
forum: General Help
---

### Post by easybe on 2012-05-17
I am trying to download Ubuntu successfully as a dual boot with Windows 7. I made a CD for it but for some reason when I select Ubuntu from the boot manager the installation will come up I can either wait for the timer to complete or go through GRUB and select an option from there (I did both, no success), and once I select an option the screen goes blank. Suggestions?


Thanks 
Mika     :KS

---

### Post by wilee-nilee on 2012-05-17
Sounds like you have made the install from Windows, a wubi install, and when you finally get to the grub menu from the widows boot menu you get a blackscreen upon choosing ubuntu is this correct?

If so has it ever boot since the install from windows?

---

### Post by easybe on 2012-05-17
> **wilee-nilee said:**
> Sounds like you have made the install from Windows, a wubi install, and when you finally get to the grub menu from the widows boot menu you get a blackscreen upon choosing ubuntu is this correct?

If so has it ever boot since the install from windows?


Yes that is correct, I tried installing it on my hard drive first but it didn't work. I tried the CD I burned and it still didn't work. Also I tried the help with CD option as well and it still goes to a blackscreen. 

No, it hasn't booted since I installed it from windows.

It worked on Windows Vista (other laptop), when installing through the hard drive, but that computer still needs cleaning up on.

---

### Post by oldfred on 2012-05-17
What video card/chip does your computer have. Often an issue with video modes. Try with liveCD first to see if it then works with the nomodeset boot parameter. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by easybe on 2012-05-18
> **oldfred said:**
> What video card/chip does your computer have. Often an issue with video modes. Try with liveCD first to see if it then works with the nomodeset boot parameter. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I have an Intel (R) HD Graphics Family (adapter string Intel (R) HD Graphics 3000). I will try this out. Do you also think a virtual machine will work

---

