---
title: "Computer shuts down while booting"
date: 2010-06-05
forum: General Help
---

### Post by curiousDood on 2010-06-05
I've been using Ubuntu for about one year. Recently upgraded to 10.04. 

The PC tries to boot, comes to the "Booting from device hd..." screen and then shuts down. It shuts down or halts but doesn't power off. The CPU is still powered. This happens for about 2 in 4 boots.

The recovery mode runs just fine. It says no damaged partitions. Only the 'booting from device' is the problem point.

If anyone had this problem before, I'd like to know the solution. Maybe some settings have to be tweaked somewhere.

---

### Post by oldfred on 2010-06-05
Is it really the monitor turning off? On my system I installed from a USB key and I could see it still flashing (installing) but the monitor went to sleep. It did the same on the install.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

