---
title: "Flash Drive Backup"
date: 2011-06-09
forum: General Help
---

### Post by TheAJGman on 2011-06-09
I'm running Ubuntu 11.04 and would like to know how to backup a whole flash drive to a single image.

---

### Post by TeoBigusGeekus on 2011-06-09
```
mkisofs -o /path/image.iso -J /media/mount_point
```
Make the necessary replacements of course.

---

### Post by TheAJGman on 2011-06-09
no i mean whole drive not just partion

---

### Post by seawolf167 on 2011-06-09
[Clonezilla]("http://www.clonezilla.org")

---

### Post by TeoBigusGeekus on 2011-06-09
In that case, you can use dd
```
dd if=/dev/sdb of=/path/image.iso -bs=1M
```

---

### Post by TheAJGman on 2011-06-09
wont work

---

### Post by TeoBigusGeekus on 2011-06-09
What and why?

---

### Post by TheAJGman on 2011-06-09
got it working had to get rid of 
-bs=1M

---

### Post by TeoBigusGeekus on 2011-06-09
Oh crap, mea culpa, it should have been
```
dd if=/dev/sdb of=/path/image.iso bs=1M
```
without the dash.
If you see that it takes too long, try again with the block size option (bs=1M). It will speed things up; you can even try to increase it (2M, 3M, etc.)

---

### Post by TheAJGman on 2011-06-09
how would i write this image to a usb

---

### Post by TeoBigusGeekus on 2011-06-09
Just copy and paste, or
```
cp /path/image.iso /media/mount_point_of_usb
```

---

### Post by Joe of loath on 2011-06-09
> **TeoBigusGeekus said:**
> Just copy and paste, or
```
cp /path/image.iso /media/mount_point_of_usb
```

Won't work.

You'll have to run

```
dd if=/location/of/image of=/dev/drive
```

However, this will only work on USB sticks of the same size. For more flexibility, clonezilla is best.

---

### Post by TheAJGman on 2011-06-09
thanks

---

### Post by TeoBigusGeekus on 2011-06-09
> **Joe of loath said:**
> Won't work.

You'll have to run

```
dd if=/location/of/image of=/dev/drive
```



If the op meant how to *extract* the image to a usb, then yes, that's the way to do it.

The usb doesn't have to be the same size as the original one; it just must be of equal or greater size to the image.

---

### Post by TheAJGman on 2011-06-09
i meant to write on to a USB of greater size

---

### Post by TeoBigusGeekus on 2011-06-09
Then 
```
dd if=/path/image.iso of=/dev/sdb
```
as Joe of Loath mentioned.
This will extract the iso to the sdb device (replace as applicable).

---

