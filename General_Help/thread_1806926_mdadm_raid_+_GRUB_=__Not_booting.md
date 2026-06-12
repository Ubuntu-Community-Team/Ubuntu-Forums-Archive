---
title: "mdadm raid + GRUB =  Not booting"
date: 2011-07-18
forum: General Help
---

### Post by sajon on 2011-07-18
I have a raid5 on 10 disk, 750gb and it have worked fine with grub for a long time with ubuntu 10.04 lts.

A couple of days ago I added a disk to the raid, growd it and then resized it.. BUT, I started the resize-process on a terminal on another computer, and after some time my girlfriend powered down that computer!
So the resize process cancelled in the middle and i couldn't acess any of the HDDs so I rebooted the server.


Now the problem, the system is not booting up, simple black with a blinking line.
Used a rescue CD to boot it up, finised the resize-process and the raid seems to be working fine so I tried to boot normal again. Same problem.

Rescue cd, updated grub, got several errors:
error: unsupported RAID version: 0.91.

I have tried to purge grub, grub-pc, grub commmon, removed /boot/grub and installed grub again. Same problem.

I have tried to erased mbr (# dd if=/dev/null of=/dev/sdX bs=446 count=1) on sda (ide disk, system), sdb (sata, new raid disk). Same problem.

Removed and reinstalled ubuntu 11.04 and is now getting error: no such device: (hdd id).

Again tried to reinstall grub on both sda and sdb, no luck.
update-grub is still generating error about raid id 0.91 and is back on a blinking line on normal boot.


When you'r resizeing a raid MDADM changed the ID from 0.90 to 0.91 to prevent something that happend happened. But since I have completed the resize-process MDADM have indeed changed the ID back to 0.90 on all disks.

I have also tried to follow a howto on a similar problem with a patch on [http://ubuntuforums.org/showthread.php?t=1573192&highlight=raid&page=6](http://ubuntuforums.org/showthread.php?t=1573192&highlight=raid&page=6)
But I cant compile, various error about dpkg.



So my problem is, I cant get grub to work. It just gives me a blinking line and unsupported RAID version: 0.91.

Please help, I really dont know what to do next..

---

### Post by dino99 on 2011-07-18
seems to have a workaround:

[http://ubuntuforums.org/showthread.php?t=1580024](http://ubuntuforums.org/showthread.php?t=1580024)
[http://ubuntuforums.org/showthread.php?t=1573192&highlight=raid](http://ubuntuforums.org/showthread.php?t=1573192&highlight=raid)

---

### Post by sajon on 2011-07-18
Some magic happend, installed lilo on ALL disks, purged it becoz it didnt work, reinstalled grub on ALL disk and now it's booting correctly =).

---

