---
title: "Resize active ext4 partition"
date: 2009-08-20
forum: General Help
---

### Post by nortexoid on 2009-08-20
I installed Jaunty on one partition and XP on another NTFS partition. It turns out the Jaunty partition is too small and I've run out of space. I've managed to resize the NTFS partition using gparted but now I can't resize the ubuntu partition from within Ubuntu using gparted since it shows the partition to be "locked" (keys icon).

I imagine it has to be unmounted before it can be resized. Is that right? If not, is there a way in Ubuntu to resize it while it's mounted? (I don't have my live cd with me as I'm on vacation.)

---

### Post by Cheesemill on 2009-08-20
You have to use the Live CD. You can't alter a mounted partition and there's no way of booting an installed Ubuntu without mounting the root partition.

---

### Post by 4t0m1c_w07f on 2009-08-20
What you can do, is go here: [HTML]http://gparted.sourceforge.net/download.php[/HTML] and download the GParted iso and burn to cd or usb..

---

### Post by SiberianBear on 2009-08-20
You can also do things properly, and manage your disks via LVM instead.

---

