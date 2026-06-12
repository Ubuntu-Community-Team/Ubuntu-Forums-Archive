---
title: "Need to rename partition or learn to command GRUB"
date: 2006-04-15
forum: General Help
---

### Post by Mr. Picklesworth on 2006-04-15
Okay, I managed to break Ubuntu. ](*,) 

Not completely broken, thankfully, and I happen to have burned a GParted Live CD that very day.

What happened was, excited about my finally working wireless network, I decided to download every package I could find to play around with.

Well... that was a bad idea.

I downloaded the kubuntu-desktop package... everything went fine; no error messages or complaints.

Upon restarting the computer, however, it looked like Kubuntu had been installed (barely, I suppose), but I became unable to log in except through in terminal mode due to a lack of drive space. (Sorry, I don't have the exact message handy; I'll edit it in in a minute -- I may be completely wrong as to what my problem is -- I recall it's the X window system telling me that it's unable to write a file due to drive space issues).

I restart with the GParted live CD, and start rearranging my partitions.
I resized my /dev/hdb2 partition (judging by exploration, the right partition -- and it was nearly full) by shrinking some other partition which barely contained anything, copying /dev/hdb2 into the new empty area, then resizing it to be nice and big and assigning it the "boot" flag.

The problem now is that the new partition which I want to be my main partition has been renamed to /deb/hdb4, so Ubuntu is still booted from the old one and thus nothing is fixed.
How can I rename this partition to /dev/hdb2, or tell GRUB to use /dev/hdb4?



Thanks in advance!

---

### Post by z_diver on 2006-04-15
[QUOTE=Mr. Picklesworth]
The problem now is that the new partition which I want to be my main partition has been renamed to /deb/hdb4, so Ubuntu is still booted from the old one and thus nothing is fixed.
How can I rename this partition to /dev/hdb2, or tell GRUB to use /dev/hdb4?
![/QUOTE]
Edit: As David pointed out below, renaming is not the way to do this.
But changing grub to boot from the correct partition should not be a problem.  You can use 'e' at the grub menu to edit the grub entries.  This will be temporary and you will have to edit /boot/grub/menu.lst when you finally get on the system.  Editing through the grub interface is somewhat cryptic but works.  Press b to boot the system once you are done.

Alternatively using an Ubuntu live CD, mount the /dev/hdb2 partition somewhere like /mnt/ -- this can be done in System > Administration > Disks. Then sudo gedit /etc/mnt/boot/grub/menu.lst and change it to point to the right partition.  Once you get used to how grub works you will find it to be unbelievably flexible.

---

### Post by dcstar on 2006-04-15
[QUOTE=Mr. Picklesworth]
......
How can I rename this partition to /dev/hdb2, or tell GRUB to use /dev/hdb4?

Thanks in advance![/QUOTE]
I doubt you can "rename" a partition as that designation is the physical location of the partition information on your disk - you would have to remove the hdb4 partition and recreate it as the second partition (assuming that area is vacant) with exactly the same information - tricky!

Editing /boot/grub/menu.lst is easier - either via the bootup options or mounting from a rescue disk.

---

