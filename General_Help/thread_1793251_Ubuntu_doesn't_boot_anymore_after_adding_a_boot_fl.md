---
title: "Ubuntu doesn't boot anymore after adding a boot flag to the Windows drive"
date: 2011-06-29
forum: General Help
---

### Post by name7ess on 2011-06-29
I have Ubuntu 10.10 installed on one (physical) hd and on the other one Windows. On both drives grub is installed to boot both operating systems. When I wanted to install SP1 for Win 7 I had to add a bootable flag to the partition from which Windows boots, otherwise the installation of SP1 does not work. I did so by booting into Ubuntu and using gparted to add this flag. After doing so the update for SP1 worked without any problems.

When trying to boot back into Ubuntu grub complained that it couldn't find the kernel anymore! I tried to boot into a Ubuntu minimal cd and to restore grub using chroot, update-grub and grub-install which didn't work. I still had the problem that it was Unable to boot Ubuntu putting me in some minimal system called initramfs. It seems however that the uuid of the partitions changed. I guess this happened when I added the bootflag to the windows disk.

Next thing I tried was to tell grub not to use the uuid for loading the kernel by uncommenting something in /etc/default/grub. Then I got the kernel booting but it suddenly stops (I guess when it is trying to mount the root file system) saying that the concerning uuid does not exist putting me into initramfs again. The strange thing is that there I coulnd't even manage to mount the root partition using /dev/sdb1 (on which it is in my case).

I would be glad if there is a way to restore the system again without having to reinstall it.

---

### Post by Rubi1200 on 2011-07-01
Hi,
in this situation, the best thing to do so we can get a better overview of the current state of the system is the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

