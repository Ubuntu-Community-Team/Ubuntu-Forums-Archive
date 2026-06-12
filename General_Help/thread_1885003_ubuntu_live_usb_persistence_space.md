---
title: "ubuntu live usb persistence space?"
date: 2011-11-22
forum: General Help
---

### Post by paul3200 on 2011-11-22
just a quick question what is the maximum amount of persistence space you can have on a Live USB? 
i have a 16gb USB and it only lets me have 4gb persistence

---

### Post by ajgreeny on 2011-11-22
That 4GB is the limit because the live USB is on a fat32 drive, I am afraid.  It is a limit of the filesystem, not the persistent USB itself, and I'm not aware of any way to change that, nor the filesystem type you use for a live USB.

---

### Post by paul3200 on 2011-11-22
so i wont be able to change it to ntfs and it will be bigger

---

### Post by ajgreeny on 2011-11-22
> **paul3200 said:**
> so i wont be able to change it to ntfs and it will be bigger
I don't think you can.

---

### Post by paul3200 on 2011-11-22
i will try it

---

### Post by efflandt on 2011-11-22
If you have a large enough USB stick that you want larger persistent data than 4 GB, why not just do a regular install to the USB stick with a Linux file system (maybe ext2 which is not a journal file system, but would minimize writes to flash which have to erase a block before it can be written to).

Just make sure that you use **manual partitioning** during install which would allow you to **put grub on the USB stick** (and be certain that you do that). Then you would have a real Linux system that could make use of additional video drivers and system updates. A full install would also be more secure since you could require login instead of having default user "ubuntu" who could do virtually anything without login from live iso.

You cannot update things like kernels or video drivers or anything else that happens early during boot on live iso on USB because it boots from a fixed squashfs filesystem before persistent data is mounted.

---

### Post by Megaptera on 2011-11-22
This gives a seperate ntfs partition and seperate persistent Ubuntu install on 4gb pen drive:
[http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess](http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess)

hope this helps?

---

