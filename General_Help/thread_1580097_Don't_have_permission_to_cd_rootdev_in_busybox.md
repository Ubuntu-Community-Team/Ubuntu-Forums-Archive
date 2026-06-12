---
title: "Don't have permission to cd /root/dev in busybox"
date: 2010-09-22
forum: General Help
---

### Post by devinfoley on 2010-09-22
I am running Ubuntu 10.04.  The operating environment fails to load and i am at busybox shell.  I don't have permission to boot or cd /root/dev for some reason.  How to get root priveleges from in busybox shell.

---

### Post by psusi on 2010-09-22
> **devinfoley said:**
> I am running Ubuntu 10.04.  The operating environment fails to load and i am at busybox shell.  I don't have permission to boot or cd /root/dev for some reason.  How to get root priveleges from in busybox shell.

You have them.  You aren't logged in if you are at a busybox shell, so you are root.  My guess is that you don't have /root mounted is the problem, so there is no /root/dev.  Not having /root mounted would be the reason you landed at the busybox shell in the first place.

---

### Post by devinfoley on 2010-09-23
well i can cd /root fine. but when i ls it shows nothing.  when i go to mkdir /root/dev it says the directory already exists. so when i try and cd /root/dev it fail because i don't have proper permissions.  is there a way to get superuser/root priveleges from in busybox shell?  i tried unmounting and remounting everything and still fail.  i will post exact failure message later today.

---

### Post by QLee on 2010-09-23
[QUOTE=devinfoley] well i can cd /root fine. but when i ls it shows nothing. [/QUOTE]
Well, you shouldn't be able to with the command you stated, a regular user doesn't have sufficient permissions to cd to root's home.


[QUOTE=devinfoley]when i go to mkdir /root/dev it says the directory already exists.[/QUOTE]
Well, once again, that command should fail because you lack sufficient permission.


[QUOTE=devinfoley] so when i try and cd /root/dev it fail because i don't have proper permissions.
...[/QUOTE]
Well, that's interesting because in a normal install there shouldn't be a /dev folder in /root.


I don't know what it is you are trying to do, but you probably don't want to be doing it in root's home folder.


Edit: another oops, forgot to add conclusion - as per previous post, due to data cited above you must have been operating as the super user at the time.

---

### Post by psusi on 2010-09-23
There are no users in the initramfs; there is only root.  /root is not root's home directory, but rather where your root filesystem is mounted before being chrooted into.  The reason ls shows nothing there is because your root fs is not mounted, which is why you got dropped to the busybox shell in the first place with the message telling you it gave up waiting for the root device.  You need to get your root device mounted in /root and exit the shell to continue booting.  Or figure out what's wrong with your kernel arguments in your grub config that are causing it not to be able to find your root and fix that.

---

### Post by QLee on 2010-09-23
[quote=psusi]...
 Or figure out what's wrong with your kernel arguments in your grub config that are causing it not to be able to find your root and fix that.[/quote]
+1

---

### Post by devinfoley on 2010-09-23
mount: mounting /dev/disk/by-uuid/536d5ce2-18d0-4228-b2f3-8386d3c4f103 on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: Target filesystem doesn't have /sbin/init
no init found. Try passing init= bootarg

Busybox Shell 1.13.3 opens and i'm at the (initramfs) prompt

---

### Post by psusi on 2010-09-23
Can you mount the fs from a livecd?  Or does dmesg show any relevant errors?  It looks like your fs may be fubar.  What kind is it?  ext3?  Or something else?

---

### Post by devinfoley on 2010-09-24
root@ubuntu:/dev# dmesg | tail
[  449.544543]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  449.544558]         1c c4 08 11 
[  449.544563] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  449.544571] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1c c4 08 08 00 01 00 00
[  449.544585] end_request: I/O error, dev sda, sector 482609169
[  449.544615] ata1: EH complete
[  449.544643] JBD: Failed to read block at offset 2
[  449.544650] JBD: recovery failed
[  449.544654] EXT4-fs (sda1): error loading journal
[  455.448208] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 103

i can't mount the fs from livecd

---

### Post by psusi on 2010-09-27
Looks like your disk has at least one bad sector, and may be failing entirely.  Fire up the disk utility, go to the smart section, and run an extended self test.  Then check the count of pending reallocations and reallocated sector count.

---

### Post by tsaowang on 2010-09-27
Hi,

At the busybox prompt, after 30 seconds or so did you hit "exit" ?

I tell you that because I also have the busybox prompt...

---

