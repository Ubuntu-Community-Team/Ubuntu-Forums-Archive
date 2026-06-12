---
title: "No graphical load bar after kernel update"
date: 2006-03-18
forum: General Help
---

### Post by Irony on 2006-03-18
I've updated my kernel;

[PHP]Commit Log for Thu Mar 16 22:44:49 2006

Upgraded the following packages:
linux-image-2.6.12-10-386 (2.6.12-10.28) to 2.6.12-10.30[/PHP]

I noticed it change my grub to hda5 (where Ubuntu used to be) however I have Ubuntu in hda2, so I changed it back.

Upon booting up the next day there was no graphical loading bar but a text load, first message being;

[PHP]can't read /lib/modules/2.6.12-10-386/initrd/vesafb.ko[/PHP]

The file is there though. It booted up okay apart from showing no graphical loading bar (login screen is as normal).

Looking at my */var/log/syslog.0* file shows;

[PHP]Mar 17 16:55:41 localhost syslogd 1.4.1#17ubuntu3: restart.
Mar 17 16:55:41 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Mar 17 16:55:41 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
Mar 17 16:55:41 localhost kernel: Symbols match kernel version 2.6.12.
Mar 17 16:55:41 localhost kernel: No module symbols loaded - kernel modules not enabled.[/PHP]

How do I get the graphical loading bar back. Any ideas?

---

### Post by Irony on 2006-03-19
Well here's the answer;

[http://ubuntuforums.org/showthread.php?t=83151&highlight=vesafb.ko](http://ubuntuforums.org/showthread.php?t=83151&highlight=vesafb.ko)
[https://launchpad.net/distros/ubuntu/+source/usplash/+bug/23502](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/23502)

[PHP]sudo gedit /usr/share/initramfs-tools/scripts/init-top/usplash[/PHP]

Change;

[PHP]	if [ $VESA = "true" ]; then
		insmod /lib/modules/`uname -r`/initrd/vesafb.ko
	else[/PHP]

To;

[PHP]	if [ $VESA = "true" ]; then
		insmod /lib/modules/`uname -r`/initrd/vesafb.ko
		insmod /lib/modules/`uname -r`/kernel/drivers/video/vesafb.ko
	else[/PHP]

Then to update initramfs;

[PHP]irony@ubuntu:~$ sudo dpkg-reconfigure linux-image-`uname -r`
Not touching initrd symlinks since we are being reinstalled (2.6.12-10.30)
Not updating image symbolic links since we are being updated (2.6.12-10.30)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done[/PHP]

This worked! I now have my graphical loading bar back; *dpkg-reconfigure linux-image-`uname -r`* though still changed my grub to hda5 but I'm not too bothered with that.

I don't know why the first link *insmod /lib/modules/`uname -r`/initrd/vesafb.ko* doesn't work as it is correct however there is a second vesafb.ko file at *insmod /lib/modules/`uname -r`/kernel/drivers/video/vesafb.ko* which does work.

---

