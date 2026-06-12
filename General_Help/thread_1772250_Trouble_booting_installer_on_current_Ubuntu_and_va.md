---
title: "Trouble booting installer on current Ubuntu and variants"
date: 2011-05-31
forum: General Help
---

### Post by Underpants on 2011-05-31
I'm having trouble getting the latest Ubuntu (or LinuxMint, or other variants based on ubu) to boot on my Dell Optiplex 740 with an nVidia 6150LE onboard graphics card. 

initrd and vmlinuz will load and things will start to roll by on the screen and then the system unexpectedly reboots itself; too fast for me to see what the last error on screen was. What can I do?

I have seem some issues where adding "nomodeset" to the grub line will get things going but I still have the issue.

I pressed TAB at the loader screen and changed the end of the line to read: 
```
boot=casper initrd=/casper/initrd.lz nomodeset --
```

What else can I try? What else can I do to diagnose this?

---

### Post by Underpants on 2011-05-31
Aynone? gurus?

---

### Post by oldfred on 2011-06-01
I have a newer nVidia and nomodeset works for me.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

the Generic setting may be another choice.
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Underpants on 2011-06-01
Ubuntu 11.04 doesn't have the same grub loader... so you have to press TAB to alter the line... I removed quiet and splash and inserted NOMODESET - it still crashes. The last line on the screen before this happens is something about **"freeing initrd memory"**

---

### Post by oldfred on 2011-06-01
If nomodeset or any of the generic settings do not work you may need additional settings or changes in your BIOS settings to get system to work.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

