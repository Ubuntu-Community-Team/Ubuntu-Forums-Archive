---
title: "Problems installing Ubuntu 10.10"
date: 2010-10-22
forum: General Help
---

### Post by THC420 on 2010-10-22
I was trying to dual-boot Windows 7(installed first) with Ubuntu 10.10 but when I tried to use GParted it wouldn't let me resize the partiton 
[IMG]http://img686.imageshack.us/img686/8936/screenshotnpe.png[/IMG]
[IMG]http://img178.imageshack.us/img178/4356/screenshot1op.png[/IMG]

What do i have to do?
Delete that window partition and reinstall window 7 first and dual boot with ubuntu later

---

### Post by ivarn on 2010-10-22
oh never mind I saw the problem now.
When you installed windows, you shouldn't have use the whole disk for that one NTFS partition.
Since the windows installation is fresh, reinstall windows but this time with a smaller partition. 20gb is enough,

---

### Post by THC420 on 2010-10-22
> **ivarn said:**
> oh never mind I saw the problem now.
When you installed windows, you shouldn't have use the whole disk for that one NTFS partition.
Since the windows installation is fresh, reinstall windows but this time with a smaller partition. 20gb is enough,

I thought as much. Thank you ivarn for clearing my doubts i'll post back on how it goes after I backup my files

---

### Post by Quackers on 2010-10-22
Is the Windows 7 system still bootable? If so go to Start then right-click Computer and select Manage. In the window that opens up click on Disk Management. This will give you a window which shows your disk layout. Right-click on your Windows 7 disk and select Shrink. This will shrink the partition to about half its present size. The resulting unallocated space at the end can then be used to install Ubuntu.

---

### Post by THC420 on 2010-10-22
Thanks you all for helping dual-boot Windows 7 and Ubuntu 10.10 your comments were helpful.

---

