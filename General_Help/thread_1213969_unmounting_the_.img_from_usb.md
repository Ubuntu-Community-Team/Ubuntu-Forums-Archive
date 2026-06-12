---
title: "unmounting the .img from usb"
date: 2009-07-15
forum: General Help
---

### Post by mammalsauceman on 2009-07-15
i am going to install unr on my acer aspire one a150 netbook, and i wanted to know if after i install using the usb flash drive, is it possible to remove the installation files or 'unmount' the image from the drive so i can use it to transfer files (which is what flash drives are made for) 

I can accept instructions for various operating systems, i am not limited to ubuntu, although it is my main operating system.

---

### Post by Cheesemill on 2009-07-15
You can just delete the files off the USB stick and use it as normal.

It will still have GRUB installed on it though, you can get rid of this by formatting the drive using [gparted]("apt:gparted").

---

### Post by TeamJ on 2009-07-15
well just deleting files will be fine for a 1gb one, buton mre it just locks off all the space, it only uses aa 1GB partition and the rest is unallocated. you will have to use a partiton manager to delete all partitions and make one new one.

---

