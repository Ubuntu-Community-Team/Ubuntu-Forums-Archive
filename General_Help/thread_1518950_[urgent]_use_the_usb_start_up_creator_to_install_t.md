---
title: "[urgent] use the usb start up creator to install to sda"
date: 2010-06-27
forum: General Help
---

### Post by markp1989 on 2010-06-27
I wana install ubuntu 10.04 in my sisters eee pc 701 2gb surf.

2gb is to small for a full install, so i wanted to use the usb start up creator to make a persistant image on the internal ssd.

i tried this, but the internal drive doesnt show up on the drives list.

how can i get the usb start up creator to show internal drives?

thanks, mark

---

### Post by btechcs on 2010-06-27
It is not possible to install ubuntu on a 2G eeepc ssd. 

1. The best way to install is to use a sd card (formatted to ext2, and mounted at /), and mount the eeepc drive (formatted to ext2, and mounted at /usr).

2. Another option is using squashfs. Create a bootable usb (persistent), and clone it to the internal ssd using dd command. assuming that usb drive is /dev/sdb1 and your internal ssd is sda1 you can clone usb to internal drive as:

```
dd if=/dev/sdb1 of=/dev/sda1 bs=4096 conv=noerror
```

PS: The 2nd option will be very slow on an eeepc, and it is better to take teh 1st option of using a SD memory card.

---

### Post by markp1989 on 2010-07-05
in the end i went with puppyeee as its alot smaller

---

