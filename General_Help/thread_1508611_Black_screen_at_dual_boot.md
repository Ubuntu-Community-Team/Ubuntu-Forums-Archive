---
title: "Black screen at dual boot"
date: 2010-06-13
forum: General Help
---

### Post by nebelspalter on 2010-06-13
Hello everybody, first of all thank you for aditting me into this forum. I am relatively new to Ubuntu ; I started 6 months ago with 9.10 and it worked fine. Recently I bought from Ubuntu.org th 10.04 version in French. The installation (dual boot with W7) went well, I personalized the software and had the "brilliant" idea to execute the recommended updates. Restarting the computer I just saw for a couple of seconds the blip up left and then a black screen. Nothing else happend. Posts to the French Ubuntu forum yielded no solution, so I decided to reinstall 10.04 again. It worked well a couple of times, and then again I had the black screen and no boot. What happens ? Do you have a solution ? How can I delete the installed versions ? Thank you for your help.

---

### Post by oldfred on 2010-06-13
Lucid seems to have some video issues.

I have a nvidia card, but the nomodeset works for at least some of the others.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)


After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line


if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

