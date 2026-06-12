---
title: "Failed Upgrade, Failed Clean Install... Ideas?"
date: 2012-04-28
forum: General Help
---

### Post by windfix on 2012-04-28
I did an upgrade from 11.10 to 12.04 on an older Gateway laptop (Celeron, 2 Gig RAM) and it appeared to go fine.  However, on reboot it hangs at the Ubuntu logo screen after GRUB menu.

Oddly, I have also tried a clean install from both USB and CD... and both are failing.  They hang at the Ubuntu logo screen after selecting Install Ubuntu - and after 2-3 minutes of disk activity.  I have tried USB 2 and USB 3 flash drives, creating the live USB from both unetbootin and from Startup Disk Creator.  I am using the 32-bit ISO.

Why would this machine suddenly become un-installable?  I've run Ubuntu on it for 3 years already.

Edit/Addition:  I was finally able to install from CD; however it still craps out on the Ubuntu logo screen when I try to boot.  I did get error messages referencing the Broadcom B43 driver, and suggesting to follow the instructions at [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware).  Unfortunately, if I boot in recovery mode (from GRUB), and attempt "sudo apt-get install firmware-b43-installer" it can not download the package (I do have a live ethernet connection).  Tried switching off wifi card, then booting, but no joy.

---

### Post by windfix on 2012-04-30
OK, solved by my Unix wizard pal.  Here's the deal: B43 is the driver for the broadcom wifi card, firmware-b43-installer is the firmware.  The former is useless, and likely causes the lockup, until the latter is installed.  So, here's how:

[LIST=1]
[*]Boot to recovery mode (select from GRUB menu)
[*]remount the root partition as read/write:  ```
mount -o remount,rw /dev/sda1
``` (or whatever your root partition is)
[*]Activate ethernet manually: ```
ifconfig eth0 up
```
[*]Now do: ```
dhclient eth0
```
[*]now: ```
apt-get install firmware-b43-installer
```
[/LIST]

And lastly, reboot.

---

### Post by mkstallings1 on 2012-05-02
Thank you so much for this.  I have been at a loss for days as to why I couldn't do a fresh install of 12.04 and get it to boot.

---

