---
title: "booting up issues"
date: 2011-01-24
forum: General Help
---

### Post by genesisends on 2011-01-24
Hello everyone, 
 
I have an IBM Thinkpad T61 laptop running Ubuntu 10.10.
Last night my screen froze while I was playing some videos. I had to press the shut down button and restart it. When I pressed and held it there was a loud beep I had not heard before. The laptop shut down and as it restarted it never entered the purple Ubuntu booting up window. It went straight to a screen that says:
 
GNU GRUB version 1.98+20100804-5ubuntu3
 
Ubuntu, with Linux 2.6.35-24-generic
Ubuntu, with Linux 2.6.35-24-generic (recovery mode)
Ubuntu, with Linux 2.6.35-23-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-26-generic
Ubuntu, with Linux 2.6.32-26-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)
 
 
 
I chose the first option (2.6.35-24-generic) and it took me to a screen that says:
 
(some numbers and letters) ? get_fs_type+0x33/0xb0
(more random characters) ? do_kern_mount+0x3e/0xe0
(more numbers) ? do_mount+0x1dc/0x220
(more numbers) ? sys_mount+0x6b/0xa0
(more numbers) syscall_call+0x7/0xb
 
some more numbers and letters displaying in pairs like 00 55 89 e5 etc)
 
end trace (some more numbers)
 
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target fielsystem doesn't have requested /sbin/init
[1.388030/ usb 5-2: new full speed USB device using uhci_hcd and address 2
No init found. Try passing init=bootary.
 
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built in shell (ash)
Enter 'help' for list of built in commands.
 
(initramfs)_
 
 
 
I'm not sure what this means, something about not being able to find the required files from my hard drive?
 
When I choose the recovery mode or a different linux version I get a similar screen. 
 
I also want to add that I've been hearing a rattling inside my laptop for the past few days and it easily overheats, which is common with thinkpads and running videos. 
 
Does anyone have advice on what I should do? I know I need to upgrade laptops but I'm trying to use this one for as long as possible. I'm comfortable with code and opening up laptops, I'm just not an expert on Linux. 
 
Thank you!
 
-G

---

### Post by davidmohammed on 2011-01-24
the mount errors dont look good.

Maybe your hard-drive has failed?

Can you boot a live CD or a live USB?  If you can, then this will point to your hard-drive as the issue.

---

