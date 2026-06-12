---
title: "USB Ubuntu 9.04 Persistent won't cold boot on desktop"
date: 2009-08-22
forum: General Help
---

### Post by rubie on 2009-08-22
Hi everyone. I'm having a problem booting [**USB Ubuntu 9.04 Persistent**]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/") on my desktop from a USB flash disk created as per instructions given on [www.pendrivelinux.com](www.pendrivelinux.com) . The problem is identical when I create the Live USB disk using the USB Startup Disk Creator booting from the CD:

The system will boot normally (and with persistence) if and only if I boot from my hard disk drive first (XP) and then do a warm reboot (no shutdown). Doing a reboot thereafter in Ubuntu, or shutting down the machine and doing a cold boot, the system will boot until the boot logo (Ubuntu) appears and the following screen of text will appear shortly therafter:

Loading /casper/vmlinuz..........................................

Loading /casper/initrd.gz........................................
........................................................ready.
Loading, please wait...
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.



BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   55.004095] FAT: unable to read inode block for updating (i_pos 26379)


Interestingly, the same Live USB disk will cold boot on my laptop. In this case though it will go through an endless reboot loop if don't shut down first (i.e. if I use the Restart option).

Can anyone shed some light on this problem? I would like to be able to cold boot Ubuntu from the USB flash drive on my desktop. Thanx

---

### Post by AmerNewbieInDE on 2009-08-22
i used usbuntu to create my live usb... didnt have a problem... look here..

[http://www.ubuntugeek.com/usbuntu-live-creator-create-liveusbs-from-windows-using-a-gui.html](http://www.ubuntugeek.com/usbuntu-live-creator-create-liveusbs-from-windows-using-a-gui.html)

---

### Post by rubie on 2009-08-23
Ok. Did you try it on 9.04 Desktop Edition?

---

### Post by rubie on 2009-08-24
Ok. I tried usbuntu, but it too causes the machine to hang on bootup - no BusyBox this time though, just a blank screen and a two flashing keyboard lights. It seems odd Ubuntu won't cold boot on this machine - Gparted does. Oh well, I guess I'll just have to boot into Windows first, then reboot to USB. Strange and annoying.

---

### Post by P4man on 2009-08-24
could it be a fault with the stick ? can you try another one?

---

### Post by rubie on 2009-08-24
I didn't think it would make any difference, but I did try it on another USB flash drive of a different brand, and it worked! I can now cold boot [**USB Ubuntu 9.04 Persistent**]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/") just as described. Thanks P4man :)

What still puzzles me is the fact that the stick I used originally did boot normally after a warm reboot from Windoze (booting first, plugging in the USB stick and then rebooting). I also did a surface test on the stick and it passes 100% - it's relatively new and unused. The same stick will cold boot on my netbook. My guess is there's a compatibility issue between Ubuntu, the desktop and the USB drive. God knows.

---

### Post by P4man on 2009-08-25
I think it has to do with the stick and bios. Got an old computer here thats not too happy booting certain sticks; when I hit the 'select boot device' key, some sticks get recognized as harddisks, some as removable (floppy) some even as USB ZIP drive. Dont remember which ones it boots, but not all of them. Not sure what causes it, stick size or something else..

---

