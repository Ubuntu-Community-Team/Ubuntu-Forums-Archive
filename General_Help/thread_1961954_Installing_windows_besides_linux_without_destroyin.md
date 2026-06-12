---
title: "Installing windows besides linux without destroying grub?"
date: 2012-04-20
forum: General Help
---

### Post by Krillezz on 2012-04-20
Is there someway I can install windows on my Ubuntu machine and then be able to choose between them at startup, the same way I get to choose when i install Ubuntu on a windows machine? I do now whish to remove Ubuntu.

Edit: nvm found this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) #-o

---

### Post by Mark Phelps on 2012-04-21
First of all, regarding your title -- NO, there is no way to install Windows without overwriting GRUB in the MBR (unless, you have separate physical drives for each OS).

To prepare for installing Windows, you will need to boot from an Ubuntu desktop CD, select Try Ubuntu, and use the GParted app to shrink your Linux partitions to leave unallocated space for Windows.

Don't format the unallocated space, just leave it as is.  Do the formatting as part of the windows install.

Then, afterward, boot from the same Ubuntu CD and use it to reinstall GRUB.

---

### Post by tmaranets on 2012-04-21
You can't install Windows along side with destroying the Grub. Your asking for a Wubi installation the opposite way. I suggest putting your files onto  a disk or usb, then install Windows, then install Ubuntu with Wubi,and then transfer your files back to Ubuntu from the disk or usb.

---

