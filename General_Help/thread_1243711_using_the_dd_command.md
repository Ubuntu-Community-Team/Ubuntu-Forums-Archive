---
title: "using the dd command"
date: 2009-08-18
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-18
i am running ubuntu off my external sata drive, and am very happy with it so far.

my question is, can i use ```
sudo dd if=/dev/sdb1 of=/dev/sda3
```

/dev/sdb1 is my external and the partition with ubuntu is 289.45G

/dev/sda3 is my internal that is only 123.14G

My internal is all windows, the third partition is only a prerelease windows 7 which i will delete. There is a little 19.54G unpartitioned space sitting. i can expand the win7 part and format swap in the rest. the thing is, i dont want grub on my main diskto mess with windows boot. is there some way to put grub on my usb flash or (if i can get it to work) my sd card?

---

### Post by andrewc6l on 2009-08-18
You can't just use dd because your source partition is larger than your destination partition. You might want to look at partimage instead (assuming you're on a file system it supports).

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

I think you can just install it as a package.

---

### Post by AmerNewbieInDE on 2009-08-18
well, thanks for the info oon dd. my understanding of it is wrong then, thought dd if=/dev/sda of=/dev/sdb had to be same size, but didnt realise even copying partitions they had to be the same.

but, i dont want to make an image of my drive, i want to actually copy it and run it on my internal. I just dont want grub on my windows drive, i want it on sd or usb

---

### Post by t0p on 2009-08-18
If you want to use dd, you must first increase the size of /dev/sda3 so it's as large as /dev/sdb1,

---

### Post by fragos on 2009-08-18
> **t0p said:**
> If you want to use dd, you must first increase the size of /dev/sda3 so it's as large as /dev/sdb1,

Can I dd a smaller partition to a larger one?

---

### Post by lavinog on 2009-08-18
> **fragos said:**
> Can I dd a smaller partition to a larger one?

I think so, but I think it would shrink the destination.

You can use gparted from the live cd to copy partitions between drives.

In the case of the op, he will have to shrink the source partition down to fit onto the other drive.

---

