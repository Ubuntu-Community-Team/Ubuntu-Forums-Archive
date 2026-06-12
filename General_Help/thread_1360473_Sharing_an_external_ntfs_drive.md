---
title: "Sharing an external ntfs drive"
date: 2009-12-20
forum: General Help
---

### Post by fizgig on 2009-12-20
Fstab currently reads:

**UUID=4EDC5DEDDC5DD037 /media/frank-usb ntfs-3g defaults,dmask=002,fmask=113,gid=plugdev,uid=frank 0 2**

It's mounted and I see frank owns the directory after being mounted:

**drwxrwxr-x 1 frank plugdev 4096 2009-12-13 13:28 frank-usb**

I try right-clicking a subfolder in it to share it.  I see it show up on a windows XP computer.  I double-click on the folder and try to enter it.  I get a name/pw box where I put in frank/pw and get denied.

Anyone know what I'm doing wrong?

---

### Post by fizgig on 2009-12-21
The drive was being mounted ok.

I had to do **smbpasswd -a frank**

and **smbpasswd -e frank** to enable it.

---

