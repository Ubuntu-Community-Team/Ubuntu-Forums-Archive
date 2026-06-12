---
title: "Saveable Ubuntu Live USB?"
date: 2011-03-31
forum: General Help
---

### Post by JoelSSK on 2011-03-31
I'm booting ubuntu from my android phone via USB and it works great, the thing is anything i install or do while using ubuntu isnt saved the next time i boot from the usb unless its saved in my phones storage.

I want to be able to keep booting ubuntu the same way but keep the programs i install there for the next time instead of starting from scratch everytime...is there something i can do?

any help is appreciated! thanks in advance!

---

### Post by C.S.Cameron on 2011-04-01
Changes are stored in a persistence file named casper-rw.
You can get a casper-rw file from pendrivelinux.com, (or elsewhere).
4GB is the maximum size as it is FAT32.
Put it in the root directory and then edit text.cfg, add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

Or you can create a ext3 partition named casper-rw of any size.

---

### Post by JoelSSK on 2011-04-01
Worked perfectly! I just used a casper-rw creator, awesome! thanks a ton! having my own operating system on my phone is super legit.

---

### Post by C.S.Cameron on 2011-04-01
If you run out of the available 4GB of space, you can make a casper-rw partition, it can be ext2, 3 or 4. If you want a separate home partition name it home-rw.

You can access the Data in the casper-rw file:
Make a directory to mount it in:
```
sudo mkdir /media/casper
```
And mount it:
```
sudo mount -o loop casper-rw /media/casper/
```

---

