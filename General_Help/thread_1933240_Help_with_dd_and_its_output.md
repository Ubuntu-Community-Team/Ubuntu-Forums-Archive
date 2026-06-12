---
title: "Help with dd and its output"
date: 2012-02-28
forum: General Help
---

### Post by 3rr0r on 2012-02-28
Can someone tell me, if I dd a flash drive to a directory on my computer, can I then just navigate that new directory as if it was my flash drive?  Or do I need some special program to open up the dd'd files?  I know dd does a bit-by-bit copy, but I'm confused as to what the output is.

Thank you.

---

### Post by cbraxton on 2012-02-28
> **3rr0r said:**
> Can someone tell me, if I dd a flash drive to a directory on my computer, can I then just navigate that new directory as if it was my flash drive?  Or do I need some special program to open up the dd'd files?

What you wind up with is a binary file containing an image of the flash drive. To mount and navigate it you would use losetup to associate the file with a loopback device and mount that. For example, if the flash drive is /dev/sdb:

```

sudo dd if=/dev/sdb of=flash_drive.img bs=2048k
sudo losetup flash_drive.img /dev/loop0
sudo mount /dev/loop0 /mount/point
ls /mount/point

```

If you just want to copy the files from the flash drive to a directory, "cp -a" would probably be preferable. Normally you would use dd to make an image for forensic purposes or possibly to make copies of a bootable flash drive. For making images I usually prefer to use ddrescue since it gives you a byte count while copying.

---

