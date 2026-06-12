---
title: "Accessing Partition while Dual-Booting"
date: 2011-06-10
forum: General Help
---

### Post by kexus on 2011-06-10
So, I installed Ubuntu using Wubi.exe for Windows.  Is there a way to access the files I have on Windows while I'm on Ubuntu?  Basically, how can I access files on the other side of the partition?

---

### Post by Rubi1200 on 2011-06-10
Hi and welcome to the forums :-)

Yes, you can:

> **How do I access the Windows drives?**

 The  Windows partition where you installed Wubi is available as /host within  Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you are using 11.04 with Unity then you can access the files by opening your Home folder and clicking on the computer icon. From there, the instructions are then the same as above.

---

### Post by ssreddy555 on 2011-06-10
The 426GB files shown in the side panel are my Windows 7 files & these can be directly accessed.

Here, Ubuntu however, is directly loaded to a partition on the hard drive. For Wubi, u will see the Win files in Host as shown above.

---

### Post by kexus on 2011-06-10
Thanks guys! :D

---

### Post by Rubi1200 on 2011-06-11
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

