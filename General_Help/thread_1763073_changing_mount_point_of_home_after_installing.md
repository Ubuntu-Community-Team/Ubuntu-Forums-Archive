---
title: "changing mount point of /home after installing"
date: 2011-05-20
forum: General Help
---

### Post by hdorath on 2011-05-20
Hello,
i just installed the new vision of Ubuntu 11.04 , i created 3 partitions 1 for swap, the other one for / and the last one for /home, but by mistake instead of selecting /home i chose /boot, and i want to change it now, i already tried changing my FSTAB and i ended up with a corrupted Desktop when i restarted. i had to change my FSTAB using VI command

 here you have a copy of my fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2ab49858-26d2-42e3-a361-39c08ef8c21e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=319fccd6-1857-4b8f-8497-0017b904de02 /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f9210388-6ebe-4121-8b7a-3cc04c57a5ba none            swap    sw              0       0



whay do i need to do? thank you in advance!

:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by oldfred on 2011-05-20
It might be quicker just to reinstall.

You have to first move all the boot & grub files & folders back into / (root) and reinstall grub, so it knows it needs to use / to boot from

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub


Then you have to move /home.

Three essentially the same ways using different commands, see which seems to make the most sense and use it.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by hdorath on 2011-05-20
thank you !!! ill let you know if that woks thank you for your quick response:P

---

### Post by papibe on 2011-05-20
If it's just a new install, I think the easiest way would be a reinstall.
Regards.

---

### Post by dcstar on 2011-05-20
> **hdorath said:**
> Hello,
i just installed the new vision of Ubuntu 11.04 , i created 3 partitions 1 for swap, the other one for / and the last one for /home, but by mistake **instead of selecting /home i chose /boot**, and i want to change it now
.......

/boot is a critical system folder which **you should not touch**.

Do a reinstall and be careful this time.

---

### Post by oldfred on 2011-05-20
dcstar is correct in that system folders are not something to normally move about.

I did move to a new /boot when using old grub, but realized I wanted a /grub partition and moved everything back. Have not done it with grub2, so there may be other hidden setting now. Again reinstall is probably the best.

I think you also have to update the fstab to remove the /boot entry before you add the entry for /home so that adds to the issues of getting all the changes in the correct place at the correct time to be able to reboot.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

---

