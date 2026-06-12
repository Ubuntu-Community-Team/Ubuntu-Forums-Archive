---
title: "how do i reserve more space for root after installation?"
date: 2010-01-28
forum: General Help
---

### Post by senchan on 2010-01-28
i installed on a partition where there is 4GB space, but when i try to install some drivers ubuntu sends me an error message that there is not enough space..so how do i get that free space inside root folder?

---

### Post by doas777 on 2010-01-28
resizing a partition is possible but requires a certain set of circumstances.
see here:
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

note: these instructions are for ext3, but shou;d carry over to 4 as well.

---

### Post by mk1w86 on 2010-01-28
You can use Gparted to resize the root partition, you might have to move or shrink some of your other partitions.

Make sure to backup any important data before resizing any partitions!!!

---

### Post by senchan on 2010-01-28
Thank you I will try to find out more about that..

---

### Post by warfacegod on 2010-01-28
If you want to use Gparted to resize your install partition, you'll need to do it from the LiveCD. Resizing a partition that Linux is using is impossible as far as I know. If were possible, I'd still say it's very bad idea.

---

### Post by senchan on 2010-01-31
> **warfacegod said:**
> If you want to use Gparted to resize your install partition, you'll need to do it from the LiveCD. Resizing a partition that Linux is using is impossible as far as I know. If were possible, I'd still say it's very bad idea.

so you suggest i format my pc and reinstall ubuntu from cd?

---

### Post by warfacegod on 2010-01-31
> **senchan said:**
> so you suggest i format my pc and reinstall ubuntu from cd?

Certainly not! Put your install disc in and boot from it. Select "Try 'buntu without changes". When it's done loading go to:

System> Admin.> Gparted (It may be called "Partition Editor")> resize the drives as you see fit> Reboot. No installing required.

Warning: have a backup of all your data. Resizing *can* be hazardous.

---

