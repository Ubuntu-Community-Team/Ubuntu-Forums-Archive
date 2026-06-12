---
title: "Add unallocated space to Ubuntu(ext4)"
date: 2010-12-15
forum: General Help
---

### Post by Toktikweb on 2010-12-15
Hi,

I want to add unallocated (17.94GB) to ext4 (ubuntu). Is it possible? And how to do this?

See attached GParted screenshot.

Thank you.

---

### Post by karthick87 on 2010-12-15
Unmount your** /dev/sda7 **and then right click on that partition ans select resize..

See the tutorial [**here**]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by Toktikweb on 2010-12-15
/dev/sda7 Unmount button is not active. (I'm in Ubuntu Live CD)

I can't enlarge /dev/sda7. See screenshot.

---

### Post by oldfred on 2010-12-15
You can either make a new /home partition and move /home into that.

Or you can move swap and then move your linux partition. Just that I do not like moving partitions left as the start often is more critical. It should work. But in case be prepared to reinstall grub. If you delete swap or move things too much it may change UUID. If UUID do change then you also have to edit fstab.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

### Post by Toktikweb on 2010-12-15
SOLVED.

1. removed swap
2. enlarged ext4
3. added swap
4. chroot-ed to Ubuntu.
5. changed UUID in /etc/fstab
6. grub reinstalled

Done :)

---

