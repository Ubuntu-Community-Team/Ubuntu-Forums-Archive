---
title: "Ubuntu 10.04.1 won't boot to CD or USB"
date: 2010-09-03
forum: General Help
---

### Post by jackmandu on 2010-09-03
I downloaded Ubuntu 10.04.1-i386 today.  When I try to boot to the CD I burned, it starts to boot and then it hangs.  The display loses signal and the monitor goes to sleep.  I created a virtual machine so I could make a USB install and the USB does the same thing. 

Biostar G41-M7
4GB Patriot DDR2
ATI Radeon HD 5670

---

### Post by oldfred on 2010-09-03
I have nvidia & had to do this to prevent my monitor from going to sleep (also in Maverick):
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by jackmandu on 2010-09-03
OK - I'll try it and see what happens.  Thanks for your response.

---

### Post by jackmandu on 2010-09-03
No go.  Still does the same thing.  The whole thing just seems to stop dead.  Should I try downloading an older ISO?

---

### Post by oldfred on 2010-09-04
Did you try each of the alternatives nomodeset, xforcevesa & radeon.modeset=0. Different versions may require different settings.

Also you can try f4 which should give a minimal graphics boot.

---

### Post by C.S.Cameron on 2010-09-04
Check the MD5SUM of the downloaded iso.

---

### Post by krimzonstarr on 2010-09-05
> **C.S.Cameron said:**
> Check the MD5SUM of the downloaded iso.

Second this. I have had MANY problems downloading linux .iso's, especially when not using torrents (which are supposed to autocheck integrity). Usually the "Live" version will work fine, but problems with installation. Always check the md5sum/sha256sum before burning to CD/LiveUSB.

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by DrKay on 2010-09-05
I've had the same difficulty. I was trying to boot a usb stick .iso of 32-bit Ubuntu 10.04.1. I would get the ubuntu slash screen with the dots moving across the bottom of the logo, but it would go on and on for an hour without ever booting beyond this.

Has anyone filed a bug on this yet?

I don't know how to check the MD5SUM, but I tried several downloads and two different usb sticks. The alternative download does work, however, but not the main one.

---

### Post by MooPi on 2010-09-05
I have a Windows 7 gaming rig that won't boot the usb Ubuntu install that has worked on every other machine I've tried. The connection with your situation is the newer ATI/AMD video card. I have a 5870. Screen goes black and stays that way.

---

### Post by dacman48 on 2010-09-05
i have this same problem. i can see the boot screen, i see the ubuntu screen with the moving dots, and then it goes blank. i know its a good cd, it just wont work

---

### Post by krimzonstarr on 2010-09-05
Not sure if I am hitting the right target here... but is this your bug? [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") Seems a lot of people are having luck with the "Workaround A."

---

### Post by jackmandu on 2010-09-06
I found one work around.  I have an older 9.10 ISO and it boots and runs just fine.  I installed and upgraded to 10.04.  It then booted in low graphics mode on its own.  Once I installed the Catalyst drivers from ATI everything was fine.  The upgrade took a couple of hours.  There must be a way to get the 10.04 iso to work when the 9.04 works just fine.  Why the regression from the old ISO to the new?

---

