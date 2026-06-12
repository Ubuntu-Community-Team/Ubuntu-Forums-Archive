---
title: "Help with Ubuntu on a custom built desktop"
date: 2012-10-12
forum: General Help
---

### Post by kaamady on 2012-10-12
Hi, I have a friend who wants Ubuntu 12.04 LTS (32-bit) on his desktop computer, which is custom built (we have no specs of what's inside) and I installed ubuntu along side Windows using a dvd that I burned and after the installation was complete on his computer, we created an account for him. it then asked us to reboot, and after we rebooted, it told us to remove any installation devices and hit enter. We removed the disc out of the tray, closed it, and hit enter. But it did nothing. So after about 20 minutes of nothing, we restarted it, and Grub never came up, but instead it went to the windows has failed to boot. It asked us to select to start windows normally, or some other options such as safe mode, Or to boot from the Windows installation disc and click on repair windows. We don't have the Windows disc...... But we let it boot normally into windows and it worked fine. So we turned it off, and booted it from the Ubuntu installation disc and when we did that, it acted like ubuntu was never installed on the computer, it gave us the option of trying it out or installing it. How do we get: A. Ubuntu to Boot up, and, B. to get grub to work?

Please help us! 
And I would really need to have a solution by Saturday :/

Ps. I couldn't get the computer to boot from a flash drive.  And Windows Vista Ultimate is installed.

Thanks in advance :P

---

### Post by kaamady on 2012-10-12
PPS. My last resort would be to go in on the windows side and delete the Linux partitions, then remove the grub bootloader. Then maybe try to re-install.

---

### Post by Rexilion on 2012-10-13
My guess is that you made a mistake installing GRUB (the bootloader).

You should install GRUB connected to the MBR of the disk (e.g. sda) and not the partition (sda4).

GRUB will handle booting and should also show a line for Windows XP so you can dualboot.

The fact that Ubuntu is not signalling anything the second time you insert the disk does not mean it is not installed.

The LiveCD just will not touch your disk without your permission/directives which is a good thing (think about it). This includes trying to be smart about detecting old installations.

---

### Post by westie457 on 2012-10-13
Boot your system using the install media into the live desktop 'Try Mode'. Plug in an ethernet cable if your wireless does not work out of the box the cable will be necessary.

Go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) on that page follow the directions for the 2nd option to install.

If it does not work please post the url for the bootinfoscript that will be generated. The boot script will give us more information for further ideas to help you.

Thank you

---

