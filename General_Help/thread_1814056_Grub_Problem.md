---
title: "Grub Problem"
date: 2011-07-28
forum: General Help
---

### Post by Hovercat on 2011-07-28
I just added a 3rd hard drive, but now when I boot my computer grub doesn't load at all, it just boots to Windows. I've tried holding down Shift, and I've tried holding down ESC but it didn't work. I believe I have grub2.

Help appreciated! :)

Edit: I did make sure the priorities were correct in the BIOS.

---

### Post by Hovercat on 2011-07-28
Problem solved! Turns out grub was installed to a different hard drive.

Thanks for the no replies, everyone!

---

### Post by oldfred on 2011-07-29
Grub defaults to install to sda. If installing with multiple drives you have to use manual install and then you get a combo box to choose which drive's MBR to install grub2's boot loader to.

You should install grub'2 boot loader to the same drive as Ubuntu is installed into and change BIOS to boot that drive.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

