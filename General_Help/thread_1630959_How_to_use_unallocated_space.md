---
title: "How to use unallocated space"
date: 2010-11-25
forum: General Help
---

### Post by hiphopapotmas on 2010-11-25
Hello, I recently deleted my partition of Windows 7 and am now only using Ubuntu. The problem occurs when i try to resize my partition to include the now unallocated 370 GB that used to be windows. When i boot from a live cd of ubuntu 10.04 and go into GParted, I right click and hit resize and it will not let me increase the size of the existing ubuntu partition. How do i go about doing this? Any help is greatly appreciated.
Sincerely, Austin

---

### Post by garvinrick4 on 2010-11-25
> **hiphopapotmas said:**
> Hello, I recently deleted my partition of Windows 7 and am now only using Ubuntu. The problem occurs when i try to resize my partition to include the now unallocated 370 GB that used to be windows. When i boot from a live cd of ubuntu 10.04 and go into GParted, I right click and hit resize and it will not let me increase the size of the existing ubuntu partition. How do i go about doing this? Any help is greatly appreciated.
Sincerely, Austin Take a screen shot of gparted and use the attach tool and post
it to this thread. Users can see your setup then.

---

### Post by hiphopapotmas on 2010-11-26
found it

---

### Post by hiphopapotmas on 2010-11-26
> **garvinrick4 said:**
> Take a screen shot of gparted and use the attach tool and post
it to this thread. Users can see your setup then.
here is a picture

---

### Post by Mark Phelps on 2010-11-26
That's because the Ubuntu partition is inside an Extended partition.

You have to resize the outer Extended partition first.

Then, you can resize the Ubuntu partition.

In both cases, however, you will have to ensure that the partition is not mounted.

---

### Post by hiphopapotmas on 2010-11-26
> **Mark Phelps said:**
> That's because the Ubuntu partition is inside an Extended partition.

You have to resize the outer Extended partition first.

Then, you can resize the Ubuntu partition.

In both cases, however, you will have to ensure that the partition is not mounted.

Thanks for the help, I was able to consolidate the partitions.

---

### Post by wojox on 2010-11-26
Click on /dev/sda3 and you should be able to resize it then. You doing this from a Live CD right?

---

