---
title: "GParted - partition full after resize"
date: 2009-11-14
forum: General Help
---

### Post by m4g1c on 2009-11-14
i had my linux partition as sda6 with 10gb of unallocated space after it. i used gparted to resize sda6 to include the extra 10gb. when it was resizing, it gave an error, told me to check the disk using fsck. i did that, tried resizing again, same error but this time in gparted it shows sda6 as being the new size (the extra 10gb is added on making the total 12gb) but it says 11.97gb is used and 101.12mb is unused. its saying the partition is full when the partition only had about 2gb of data on it before.

why is this happening? how do i get rid of that "used" space so my sda6 will only have 2gb used? thanks

---

### Post by undecim on 2009-11-14
I don't supposed you saved a copy of the exact error? I believe gparted has an option to export a log when there is an error. Without that information, there isn't much that anyone can do to help you.

Filesystem problems can get really ugly. It would be best, if possible, for you to backup all your data to an external drive and use gparted to completely erase the filesystem and create a new one.

If that's not possible, then I need more information in order to help you.

What type of filesystem is it? ext3 is the default on Ubuntu before 9.10 and ext4 is the default for 9.10, so unless you specified otherwise during installation, it will be one of those two.

Can you tell me anything else about the error? What the error said, at what point in the resize process it happened, etc.

---

### Post by m4g1c on 2009-11-14
> **undecim said:**
> I don't supposed you saved a copy of the exact error? I believe gparted has an option to export a log when there is an error. Without that information, there isn't much that anyone can do to help you.

Filesystem problems can get really ugly. It would be best, if possible, for you to backup all your data to an external drive and use gparted to completely erase the filesystem and create a new one.

If that's not possible, then I need more information in order to help you.

What type of filesystem is it? ext3 is the default on Ubuntu before 9.10 and ext4 is the default for 9.10, so unless you specified otherwise during installation, it will be one of those two.

Can you tell me anything else about the error? What the error said, at what point in the resize process it happened, etc.

yes i know i should have logged the error. the thing is, it happened multiple times and kept putting my partitions back as if nothing had happened but this time it "appears" that the partition was extended but the "extra space" is full

i want to avoid erasing the filesystem if i can, that will be a last resort

it was an ext3 filesystem

the error happened at the VERY END of the process. i recall there being a list of all the processes that were gone thru and they all had a checkmark except the last one. i think it was the part where it was actually growing the partition. the error said to run "e2[something] fsck /dev/sda6" or something similar to that (which i did run) i know im not being very helpful in not having the exact error, i will try to resize the filesystem and see if i can reproduce it again

---

### Post by jeb800e on 2009-11-14
A clean install may fix the problem. You can also try a program called DBAN (dban.org) to completely erase nearly everything on your hard disk.

---

### Post by undecim on 2009-11-15
> **jeb800e said:**
> A clean install may fix the problem. You can also try a program called DBAN (dban.org) to completely erase nearly everything on your hard disk.

There's no need to use dban. A simple format would be the best option

---

### Post by m4g1c on 2009-11-15
> **undecim said:**
> There's no need to use dban. A simple format would be the best option

looks like ill have to do a new install. if anyone has any more suggestions on possibly fixing it please do

too late, i deleted the partition and reinstalled, now it looks fine

---

