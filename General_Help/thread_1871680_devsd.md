---
title: "/dev/sd??"
date: 2011-10-29
forum: General Help
---

### Post by aeronutt on 2011-10-29
I have a usb disk that when I plug it in, sometimes shows up as /dev/sdc and sometimes as /dev/sdb. 

Is there a way to control which /dev it shows up as?

(Note, this is before mounting, this is immediately after plugging in and using sudo fsdisk -l)

---

### Post by nothingspecial on 2011-10-29
mount it by uuid

To find out what it is type ```
sudo blkid
```

That doesn't change.

---

### Post by aeronutt on 2011-10-29
> **nothingspecial said:**
> mount it by uuid

To find out what it is type ```
sudo blkid
```

That doesn't change.

Thanks, yea, I forgot to mention that I'm mounting via truecrypt, and it seems truecrypt doesn't understand UUID.  That is, this didn't work:

truecrypt -t -k "" --protect-hidden=no UUID=<usbdiskuid> /media/truecrypt

I'm finding something about using a path such as "/dev/disk/by-{id,path}" ?

---

### Post by ajgreeny on 2011-10-29
I don't know if truecrypt will affect this, but if you give the partition on the disk a label, the mount point will be a folder with the same name as the label.

For example an unencrypted flash drive with a single partition with label KINGSTON will automount to /media/KINGSTON, no matter what the /dev/sdx# name is.

---

### Post by aeronutt on 2011-10-29
Ok, by id worked, don't know why by uuid doesn't. So, for others reference, finding the id in /dev/disk/by-id, then simply use that path in truecrypt, eg:

truecrypt -t -k "" --protect-hidden=no /dev/disk/by-id/<disk-id> /media/truecrypt

---

