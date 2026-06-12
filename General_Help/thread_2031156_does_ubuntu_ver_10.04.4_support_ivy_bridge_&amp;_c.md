---
title: "does ubuntu ver 10.04.4 support ivy bridge &amp; chipset z77? ubuntu 12.04 destory laptop"
date: 2012-07-21
forum: General Help
---

### Post by creatxr on 2012-07-21
does ubuntu ver 10.04.4 support ivy bridge & chipset z77? 
i am so disgusted with ubuntu ver 12.04.
i cannot install it within graph mode , so i take long time to install it with alternate version.
it seems it has been installed successfully yesterday, but when i start my desktop today it failed.
i don't love Unity but it used as the default GUI.

the most terrible thing is that "ubuntu 12.04 destory my laptop".
i don't know what happended.
at that time, i used the usb boot key which made by ubuntu 12.04,
it cannot start the gui install mode and stay black screen for long time.
so i press power button for 30 sec to shutdown my netbook.
after that, my netbook 's lcd is always black.
i try to reset bios.
but it helps nothing.
my netbook is dead.
:confused:

---

### Post by oldfred on 2012-07-21
I would doubt that 10.04 would support the new hardware. 

Did you install in UEFI/gpt mode or BIOS/mbr mode? 

The new systems have two ways to boot from the UEFI menu and whichever you use determines the way it is installed. Not sure from alternate install whether it can do both or not?

Can you get to UEFI menu? If so then Ubuntu did not do anything to system. And Ubuntu does not change UEFI (new systems have UEFI that may offer BIOS settings).
But most new systems do have video issues and need boot parameters or other settings to work.

This says 12.04 has good support for ivy bridge. But laptops are often unique. What laptop is it?

[http://www.phoronix.com/scan.php?page=article&item=intel_z77_chipset&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_z77_chipset&num=1)

---

### Post by creatxr on 2012-07-21
i installed it in efi boot, after installed, it has been successfully rebooted. 
but today it doesn't work. so i installed ver 10,04 now. it need new drivers ....  
asus sabertooth z77 i7 3770

the laptop is a acer netbook which is buy at 2008~2009.

---

### Post by oldfred on 2012-07-21
I do not understand, a z77 cannot be from 2009 or are these two different systems.

My system is dual core from 2006 and it took a year or two before Ubuntu ran well. Mostly nVidia type issues. 
My laptop is from a week before Vista (2007?) and has run Ubuntu 10.10 & I tested wtih 12.04 without major issues.

I do not think there are drivers you can install in 10.04 for a very new system. Better to try to resolve issues with 12.04.

---

