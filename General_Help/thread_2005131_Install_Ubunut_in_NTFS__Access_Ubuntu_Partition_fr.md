---
title: "Install Ubunut in NTFS?  Access Ubuntu Partition from 7 Partition?"
date: 2012-06-17
forum: General Help
---

### Post by Pareto Optimal on 2012-06-17
I installed W7 and Ubuntu long ago using instructions I found online that I can't find.  
It instructed the use of GParted in a way that I hadn't used it before.  I recall leaving empty space between partitions and I was prompted or the online page instructed me to insert each OS disc.  Both OSes were installed and I can see both OS partitions in 7.  7 shows both partitions as being NTFS.  Everything I've read lately says that you can NOT install Ubuntu in NTFS.  I think I can see the 7 partition in Ubuntu but I don't recall.  I'm able to store files in the Ubuntu partition while using 7.  I want to do the same on another laptop but it seems to be impossible.  

Please help.

---

### Post by SDX0 on 2012-06-17
I'm not sure how you were able to seemingly install Ubuntu on an NTFS filesystem in the past, but you could just format your /home partition to FAT32 on the new laptop for access to your Ubuntu files from Windows 7.

---

### Post by Shadius on 2012-06-17
I didn't think it was possible to install Ubuntu Linux on NTFS. :confused:

---

### Post by idoitprone on 2012-06-17
> **Pareto Optimal said:**
> I installed W7 and Ubuntu long ago using instructions I found online that I can't find.  
It instructed the use of GParted in a way that I hadn't used it before.  I recall leaving empty space between partitions and I was prompted or the online page instructed me to insert each OS disc.  Both OSes were installed and I can see both OS partitions in 7.  7 shows both partitions as being NTFS.  Everything I've read lately says that you can NOT install Ubuntu in NTFS.  I think I can see the 7 partition in Ubuntu but I don't recall.  I'm able to store files in the Ubuntu partition while using 7.  I want to do the same on another laptop but it seems to be impossible.  

Please help.

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

use wubi
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

@shadius and sdx0 use your imaginations while advising the op that ubuntu will inherit windows problems because ubuntu is installed on ntfs

---

### Post by coffeecat on 2012-06-17
The only way of installing Ubuntu into a NTFS filesystem is to use the wubi installer. But even with that, Ubuntu is running in a Linux filesystem. A wubi install creates a /ubuntu/disks/root.disk file (or \ubuntu\disks\root.disk as seen from Windows) which itself contains an ext4 filesystem and acts as a virtual partition. With wubi, you can install to any NTFS partition, not just the Windows C: partition. Beware, though. I've seen threads where people have created their wubi install in a "D:" partition of, say, 80GB in size, but the wubi virtual partition is only the default 8GB, and they cannot understand why they cannot use the remaining 72GB.

Be aware too that wubi installs run slower than native installations, and would be vulnerable to filesystem corruption of the host filesystem.

If you install Ubuntu natively to a pre-exisiting NTFS partition, the only way that will work is if you reformat it to a Linux filesystem first, or allow the installer to do so.

---

### Post by Cheesemill on 2012-06-17
> **SDX0 said:**
> I'm not sure how you were able to seemingly install Ubuntu on an NTFS filesystem in the past, but you could just format your /home partition to FAT32 on the new laptop for access to your Ubuntu files from Windows 7.
You can't do this. /home has to be on a partition that's formatted with a Linux filesystem (not FAT or NTFS).

---

### Post by audiomick on 2012-06-17
> **cheesemill said:**
> you can't do this. /home has to be on a partition that's formatted with a linux filesystem (not fat or ntfs).
+1

---

