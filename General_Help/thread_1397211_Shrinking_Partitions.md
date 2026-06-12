---
title: "Shrinking Partitions?"
date: 2010-02-03
forum: General Help
---

### Post by hawaiian1der on 2010-02-03
I have nothing but Ubuntu 10.04 on my laptop. I want to put 2, maybe 3, other Linux distributions to the laptop. I got a book called "Linux Bible: 2010 Edition" and it had a couple distributions that I want to have on my computer. These would be Fedora, openSUSE, and perhaps KNOPPIX. In order to do this I need to shrink the Ubuntu partition, but when I try to do it on the other distributions it says that this partition is unable to be shrunk. I went looking on the internet for an answer to what I should do and some people said to use GParted. This didn't either. What do I do?

---

### Post by x33a on 2010-02-03
hi i would suggest that if you want to try a lot of distros, then you should try virtualisation.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by bumanie on 2010-02-03
You have probably got ubuntu installed in a logical partition. Please post the output of terminal command > sudo fdisk -lLogical partitions cannot be altered in size, however, the partitions within the logical partitions can be resized etc.

---

### Post by dcstar on 2010-02-03
> **bumanie said:**
> You have probably got ubuntu installed in a logical partition. Please post the output of terminal command **Logical partitions cannot be altered in size**, however, the partitions within the logical partitions can be resized etc.

Logical Partitions **can** be resized like any other partition - all partitions within them must be unmounted to allow it.

Any resizing of Ubuntu partitions can change their UUID, which is a problem that can require manual editing of the /etc/fstab file.

---

### Post by hawaiian1der on 2010-02-03
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ba3704b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59336   476616388+  83  Linux
/dev/sda2           59337       60801    11767612+   5  Extended
/dev/sda5           59337       60801    11767581   82  Linux swap /

---

