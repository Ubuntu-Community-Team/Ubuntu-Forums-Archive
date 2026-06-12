---
title: "help fixing four gig flash drive."
date: 2010-10-06
forum: General Help
---

### Post by coolman98 on 2010-10-06
I plugged in my flash drive today and now I t won't mount is there any way to fix it here is gparted screenshot.

---

### Post by coolman98 on 2010-10-06
I tried
mount /dev/sdb

---

### Post by TeoBigusGeekus on 2010-10-06
What about:
```
mkdir ~/Desktop/flash_folder;mount /dev/sdb ~/Desktop/flash_folder

```

---

### Post by coolman98 on 2010-10-06
did not work. know any cheap 4 gig flash drives.

---

### Post by coolman98 on 2010-10-06
on ebay?

---

### Post by DarthScape on 2010-10-06
Are you worried about the data? if not, there looks like there is an option to format. did that work?

---

### Post by coolman98 on 2010-10-07
no

---

### Post by coolman98 on 2010-10-07
wont mount media not found error

---

### Post by coolman98 on 2010-10-07
umm that did not realy help but I love the indian accent

---

### Post by soldier1st on 2010-10-07
if you open gparted will it show the device or not as if it does not no matter what then it could be a problem with the device. also do you have access to a windows pc to copy the data to it. also you could try booting to a live ubuntu session and see if it detect it?

---

### Post by coolman98 on 2010-10-08
sorry I don't think it can be fixed.
thanks for helping.

---

### Post by Andy06 on 2010-10-08
You may need to redo the MBR in addition to reformatting the filesystem. 
Formatting the whole filesystem actually doesn't even touch the MBR

---

