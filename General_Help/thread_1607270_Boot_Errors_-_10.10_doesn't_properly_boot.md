---
title: "Boot Errors - 10.10 doesn't properly boot"
date: 2010-10-27
forum: General Help
---

### Post by aydee on 2010-10-27
When I Attempt To Boot Ubuntu 10.10 I get this error

mount: mounting /dev on /root/dev failed no such file or directory
mount: mounting /sys on /root/sys failed no such file or directory
mount: mounting /proc on /root/proc failed no such file or direc

target filesystem doesn't doesn't have requested /sbin/init
no init found. Try passing init= bootarg

BusyBox v1.15.3 (ubuntu 1:1.15.3-1 ubuntu4) built-in shell (ash)
enter help for a list of built-in comands

please help!!

---

### Post by drs305 on 2010-10-27
If it's a Grub2 problem, you might be able to fix it from the Grub menu:

At the Grub menu, press "c" to get to the grub prompt and type "ls" to list the partitions seen by grub. (hd0,1) (hd0,5) etc.

If you see your Ubuntu partition listed, press ESC to return to the menu, then press "e" to edit the entry.

[LIST]
[*]Use the cursor key to move to the start of the "search" line. Hold down the DEL key and remove the entire line.
[*]On the linux line, replace the "root=UUID=<uuid>" part with the correct partition designation >>  root=/dev/sdaX ......  
Example if Ubuntu is on (hd0,5):
Old:  linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro single 
New:  linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
[/LIST]

After making the change, press CTRL-x and see if it boots. If it does, when you get to the Desktop run "sudo update-grub".

---

### Post by fmigpaulo on 2010-10-27
Boot with live cd.
open terminal:

```

sudo -i

fdisk -l
Device Boot Start End Blocks Id System
/dev/sda1 * 1 3824 30716248+ 7 HPFS/NTFS
/dev/sda2 3825 14593 86501992+ 5 Extended
/dev/sda5 3825 5648 14651248+ 83 Linux ## <- This might be diferent

fsck -fy /dev/sda5

```

After that, reboot.
This could't work, take a look at [http://ubuntuforums.org/showthread.php?p=10024500](http://ubuntuforums.org/showthread.php?p=10024500)

---

