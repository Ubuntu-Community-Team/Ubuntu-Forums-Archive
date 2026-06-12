---
title: "Flash drive not mounting when on hub - AGAIN!"
date: 2009-09-04
forum: General Help
---

### Post by Thanh-BKK on 2009-09-04
Hello.

This issue i had previously with Hardy, when i plug a flash drive into my 5-port USB hub it would not mount. On Hardy i had to issue a "lsusb" via terminal which caused that drive to be detected and subsequently auto-mounted. When i plugged the drive straight into a mainboard-USB-jack it mounted immediately. After some update then this problem disappeared.

Now it's back - on Jaunty, but different. 

So plugging my flash drive into the hub does once again nothing however this time "lsusb" tells me very clearly it is there - but STILL doesn't mount. Also the "ejecter" thingy loads and tells me that my flash drive is there, but "greyed out" i.e. unmounted. It does NOT show up under "removable drives" so how am i supposed to mount that..?

And again when i plug it into the mainboard jack it mounts immediately. 

An USB hard drive DOES mount just fine when plugged into the hub - just the flash drive doesn't.

I wouldm appreciate any advice on how to fix this issue. Many thanks in advance.

Kind regards.....

Thanh

---

### Post by hal10000 on 2009-09-04
can you mount it manually from a terminal window?
First look for the device name with [COLOR="Red"]sudo fdisk -l[/COLOR]
The command is (assumed the flash drive is formatted in fat32):
> sudo mount -tvfat /dev/your_flash_device /mnt
If it works, you'll see it' content under /mnt
> sudo umount /mnt
this unmounts the device.

---

### Post by Thanh-BKK on 2009-09-04
Hi.

I will try that as soon as i am back at home (currently at work).

However the drive DOES mount (as mentioned before) when connected to the USB jack that i  directly on the mainboard, only on the hub it doesn't work. The same problem was with Hardy until some update fixed it (probably one of the kernel updates). 

Best regards....

Thanh

---

### Post by Thanh-BKK on 2009-09-04
Hi.

Now i am at home, plugged in my flash drive - and it worked..?? It auto-mounted just fine this time round..... weirdness!

Kind regards.....

Thanh

---

