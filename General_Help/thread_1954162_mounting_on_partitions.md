---
title: "mounting on partitions"
date: 2012-04-07
forum: General Help
---

### Post by aneeshnair on 2012-04-07
Dear friends, I am successfully running my ubuntu 11.10.  I have two separate partitions apart from my linux installation, one is ext4 for using as a extra storage space in linux and the other one NTFS (both in same harddisk).  Now, every time i boot, the same is shown in "My Computer" although it doesn't mount automatically.  I have checked my /etc/fstab, however it doesn't show on fstab except my /, /home and /swap partitions. When i click the link, then only it mounts to my /media folder.  I want it to be hidden on booting up.  How to accomplish this?  Why it is not showing in /etc/fstab?  What makes it mount then? 
Please help...

---

### Post by Morbius1 on 2012-04-07
You Linux OS is designed to show you these unmounted partitions allowing you to select them to mount them to /media automatically.

If you want them to mount every time you boot you can add an entry in fstab but this statement confuses me:
>  I want it to be hidden on booting up.  How to accomplish this? 
You don't want them to show up in "My Computer" but you want them to mount at boot?
You don't want them to be mount-able at all?

---

