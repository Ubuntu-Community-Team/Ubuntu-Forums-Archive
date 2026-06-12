---
title: "Ubuntu 10.10 install confusion"
date: 2010-10-02
forum: General Help
---

### Post by rmcellig on 2010-10-02
I had Ubuntu 10.04 on my Mac in Dual Boot mode. I want to clean install of 10.10 RC. I deleted the partition that my other Ubuntu OS was on so I now have 77GB of free space. When I install 10.10 I have three options.

1.Install alongside other operating systems, 
2.erase and use entire disc, 
3. specify partitions manually. 

I have Mac OS 10 in another partition. So I  have 77GB of unallocated space. Do I choose option number one to install Ubuntu 10.10?

---

### Post by rmcellig on 2010-10-02
I get an error no root file system is defined. Is this because I haven't defined the mount point? If so, what should I set the mount point to? I selected the 77BG of free space in the Allocate Drive Space Window. When I double click on it, I see the partition size, Location for new partition beginning or end (does it matter?), Use as, I have EXT 4 journaled selected, and nothing set for mount point.

---

### Post by Quackers on 2010-10-02
You should select / as the mount point.

---

### Post by rmcellig on 2010-10-02
And I can still go into my Mac partition no probleor is that not related to this?

---

### Post by Quackers on 2010-10-02
During the installation grub will be installed. Grub will find the other OS and present a menu where you can choose which OS to boot.

---

### Post by rmcellig on 2010-10-02
Works great!

---

### Post by Quackers on 2010-10-03
I'm glad it went well :-)

---

