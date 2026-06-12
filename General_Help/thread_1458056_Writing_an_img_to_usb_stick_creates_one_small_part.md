---
title: "Writing an img to usb stick creates one small partition"
date: 2010-04-19
forum: General Help
---

### Post by themusicalduck on 2010-04-19
I want to use my usb stick to boot up the Chameleon boot loader. Because grub2 doesn't support booting into Chameleon, I have to boot from my usb drive whenever I want to use it. The problem is that when I use dd to write the .img, it makes one 20mb partition on the drive with the files stored. If I try to create a second partition, it won't let me create one that is bigger than 1gb. Also, if I write the image, copy the files off it, create a new partition table and new larger partition with the same file system as before, then copy the files back over, it doesn't work. It just says "error" when booting.

This is annoying, because I have a 16gb pen drive, but I have to reformat it everytime I want to boot from it or carry files on it.

Anyone know any way to fix this? The dd command I use is ```
sudo dd if=Chameleon.img of=/dev/sdd bs=1M

```
I thought it might be something to do with "bs=1M", but looking at man dd, it doesn't look related.

---

### Post by themusicalduck on 2010-04-19
bump

---

