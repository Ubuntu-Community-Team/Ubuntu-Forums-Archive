---
title: "root disk not found"
date: 2011-05-18
forum: General Help
---

### Post by rmcclatchey on 2011-05-18
I did a CD install of 10.04 LTS (twice), sda1 is  on an adaptec 39160. I was wipeing
Win 2K and I must have lost the boot chain or MDR. The CD install appears fine
downloading for an hour or so. Then on reboot the root disk cannot be found.

ALERT: /dev/disk/by-uuid/................. does not exist.

BusyBox comes up. Then initramfs. cat /proc/cmdline gives
BOOT_IMAGE=/boot/vmlinuz............. ro quite splash

ls shows /dev/disk/by-uuid/........................

ls shows no /boot  or grub or /etc/grub/defaults/grub dirs.

I tried root-/dev/sda1

I tried rescatux, which claimed to install grub. No fix.
I'm not finding help on the adaptec site.

Do I need some SCSI drivers? How to install?

---

### Post by dabl on 2011-05-18
The product information on the Adaptec site show Linux support, but Debian (and Ubuntu) are not shown.  But one would think there is kernel support in Debian and its derivatives including Ubuntu.

If you boot a Live CD, and then issue ```
sudo fdisk -lu
```, does the drive show up?  If so, try ```
sudo blkid
``` and lets see if it is getting a UUID assignment.

Are there other hard drives in that system?  If so, possibly the installer is getting confused about where you want Grub installed.

---

### Post by rmcclatchey on 2011-05-19
The fix was to type "exit" at the initramfs prompt. I kept hitting the restart button.
One it responded exit, I wqas able to edit the boot string in /etc/default/grob to rootdelay=60.
Boots OK now.

---

