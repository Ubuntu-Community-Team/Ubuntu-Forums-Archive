---
title: "Make Link onto Desktop From Anoter Partition"
date: 2010-07-12
forum: General Help
---

### Post by gthorn on 2010-07-12
I have recently installed Ubuntu on a friend's computer so they can have a fast operating system without worrying about Security. The problem I am having is with his files.

Ubuntu is installed on its own Partition, and his Documents and files are on his old partition with Tiny XP installed on it.

There is not enough room on the Hard Drive to have copies of his music and files on both partitions, so I thought I would just make links and put them onto the desktop so he could easily access them.

The problem is, every time I restart his computer, the links to the folders become broken.


Is there some special way to Make a link to a folder on another partition?

---

### Post by dcstar on 2010-07-14
> **gthorn said:**
> I have recently installed Ubuntu on a friend's computer so they can have a fast operating system without worrying about Security. The problem I am having is with his files.

Ubuntu is installed on its own Partition, and his Documents and files are on his old partition with Tiny XP installed on it.

There is not enough room on the Hard Drive to have copies of his music and files on both partitions, so I thought I would just make links and put them onto the desktop so he could easily access them.

The problem is, every time I restart his computer, the links to the folders become broken.


Is there some special way to Make a link to a folder on another partition?

Install the **pysdm** package, set up the mount of the partition permanently and then the links will also be permanent.

---

