---
title: "Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea"
date: 2011-05-14
forum: General Help
---

### Post by joelstitch on 2011-05-14
So I just installed Windows XP on a seperate partition and now I cant boot from Ubuntu. I have done this before and been able to reinstall grub but this time I cant remember how I did it. I have tried the instructions from [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and [here]("http://www.gregledet.net/?tag=reinstalling-grub-2") but I cant get it to work. I keep getting this error:

> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


This is what I get with the full steps from the first link:

> ubuntu@ubuntu:~$ mount | tail -1
/dev/sda5 on /mnt type ext4 (rw)
ubuntu@ubuntu:~$ ls /mnt/boot
abi-2.6.32-28-generic         memtest86+.bin
abi-2.6.32-30-generic         System.map-2.6.32-28-generic
abi-2.6.32-31-generic         System.map-2.6.32-30-generic
config-2.6.32-28-generic      System.map-2.6.32-31-generic
config-2.6.32-30-generic      vmcoreinfo-2.6.32-28-generic
config-2.6.32-31-generic      vmcoreinfo-2.6.32-30-generic
grub                          vmcoreinfo-2.6.32-31-generic
initrd.img-2.6.32-28-generic  vmlinuz-2.6.32-28-generic
initrd.img-2.6.32-30-generic  vmlinuz-2.6.32-30-generic
initrd.img-2.6.32-31-generic  vmlinuz-2.6.32-31-generic
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


---

### Post by Quackers on 2011-05-14
You need to mount your Ubuntu root partition (looks like that may be /dev/sda) and if you have a separate Ubuntu boot partition mount that. Then you need to install grub to the mbr of the drive rather than to a partition.
ie 
```
sudo grub-install --root-directory=/mnt /dev/sda
``` NOT /dev/sda5 (unless you have a reason for installing to a partition - but it's not the normal way).

---

### Post by joelstitch on 2011-05-14
> **Quackers said:**
> You need to mount your Ubuntu root partition (looks like that may be /dev/sda) and if you have a separate Ubuntu boot partition mount that. Then you need to install grub to the mbr of the drive rather than to a partition.
ie 
```
sudo grub-install --root-directory=/mnt /dev/sda
``` NOT /dev/sda5 (unless you have a reason for installing to a partition - but it's not the normal way).

When I use the command **mount | tail -1  **I get this:

**/dev/sda5 on /media/d44d7cac-be0f-443b-a125-0fd1aeabcc4e type ext4 (rw,nosuid,nodev,uhelper=udisks)**

So shouldnt it be /dev/sda5? I tried using **sudo grub-install --root-directory=/mnt /dev/sda** and this is what I got:

> /usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by Quackers on 2011-05-14
Ok, it appears that you are already booted into a live cd desktop.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

