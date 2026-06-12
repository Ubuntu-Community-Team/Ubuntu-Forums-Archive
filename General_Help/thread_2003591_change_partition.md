---
title: "change partition"
date: 2012-06-14
forum: General Help
---

### Post by ernestj on 2012-06-14
I need to install Ubuntu 12.04 and want to reduce my windows partition and increase my Ubuntu partition. (I am running out of space for Ubuntu.) I went to install Ubuntu and choose "other" and am lost. How do I reduce my windows partition and increase ubuntu? I thought it would be easiest during a fresh install.

Thanks,
Ernie

---

### Post by kanikilu on 2012-06-14
If you have Windows 7, you can shrink the volume from the built-in disk manager. Otherwise, you can still do it with GParted on the Ubuntu Live CD, or with the GParted Live CD:

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by Mark Phelps on 2012-06-14
IF you're running Win7 (or Vista), do NOT use the Ubuntu installer, or any Linux utility to shrink the Windows OS partition.  These Windows versions are very sensitive to changes from "outside" (i.e., Linux) and can easily become corrupted as a result.  If that happens, you won't be able to boot into Windows anymore.

Instead, use the Win7 Disk Management utility to shrink the OS partition.  Once you have done that, reboot into Win7 a couple of times to let it make adjustments.

Also, you won't be able to make changes to your Linux partitions while you're running Ubuntu from the hard drive because they will be in use.  Instead, you will have to boot from an Ubuntu LiveCD or LiveUSB, launch GParted, and make the changes from there.

---

### Post by ernestj on 2012-06-14
Thank you. That is what I started thinking about after I made this post. I will log into Windows and use the management utility. I have not been in Windows is forever!

---

### Post by Mark Phelps on 2012-06-14
I should have mentioned that if you're running Windows XP, you should not have this problem -- as it is not so touchy with changes being made from "outside".

---

### Post by soulcat on 2012-06-14
hi

i done the same thing, but on the safe side i backed up my ubuntu partition into a image file on another hard drive. then deleted the partition extended to the required size, then tranfered the image file to the new sized partition, all done via windows 7 then i had to reinstall the ubuntu grub loader....this worked for me, but i'm no expert, i think thats the only time i use windows also check out any youtube tutorials

---

