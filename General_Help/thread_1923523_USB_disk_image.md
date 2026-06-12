---
title: "USB disk image?"
date: 2012-02-10
forum: General Help
---

### Post by brpylko on 2012-02-10
I need to be able to boot off of a flash drive in Virtualbox, and creating a vmdk that references the flash drive did not work. So I am looking for a way to create a disk image of it (format doesn't matter). I am wondering if using ```
sudo dd if=/dev/sdb of=/path/to/image
``` would work, but I don't know what type of file that would be(vdi, vhd, vmdk, etc).

---

### Post by C.S.Cameron on 2012-02-11
If it is Ubuntu on your flash drive, you should be able to make an iso image, that Vbox can load, using Remastersys.

---

### Post by brpylko on 2012-02-11
No, it is a USB stick with a customized windoze 7 installer.

---

### Post by C.S.Cameron on 2012-02-11
To make an iso image of a CD: This duplicates sector for sector. MyCD.iso will be a hard disk image file of the CD.

```

dd if=/dev/hdc of=/home/ubuntu/myCD.iso bs=2048 conv=sync,notrunc
```

I am not totally sure Vbox will be able to load this though.

---

### Post by brpylko on 2012-02-12
Thanks, but I just found out that I can use```
vboxmanage convertfromraw /path/to/image.iso /path/to/vdisk.vdi
```

---

