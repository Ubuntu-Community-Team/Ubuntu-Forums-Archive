---
title: "restoring an mbr backup to a dd image"
date: 2009-08-21
forum: General Help
---

### Post by sefs on 2009-08-21
Hey there,

I created a dd image of a block device.

This image is called sdb.img (1GB in size)

I have the mbr for this stored in mbr.bin  it is 512K in size.

I would like to restore mbr.bin to the sdb.img file

I tried dd if=mbr.bin of=sdb.img bs=512 count=1

This does not quite as it truncates the 1GB sdb.img file to 512K.

Is there a way to do it properly?

Thanks.

---

### Post by AmerNewbieInDE on 2009-08-21
assuming you are in the correct folder when you type "IF=" that looks ok, but you must tell it where to put it.. /dev/sd??? or /dev/hd???

---

### Post by sefs on 2009-08-21
> **AmerNewbieInDE said:**
> assuming you are in the correct folder when you type "IF=" that looks ok, but you must tell it where to put it.. /dev/sd??? or /dev/hd???

I dont want to restore it to an actual block device...I am working with an image of a block device called sdb.img, So its an actual img file i am trying to get the mbr in.

Thanks.

---

### Post by Lampi on 2009-08-21
keep them separate - in fact: I don't see any way how to mix the mbr file with your image.... if you restore your 1GB image into a device (say: sdb1) you can restore the mbr of sdb like this:

```
dd if=mbr.bin of=/dev/sdb bs=446 count=1
```

---

### Post by sefs on 2009-08-21
Thank you all.

---

