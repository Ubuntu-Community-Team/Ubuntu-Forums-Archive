---
title: "Moving around partitions"
date: 2012-01-26
forum: General Help
---

### Post by ryanmichaelmcclure on 2012-01-26
Here's a screenshot of my current partition layout:

[IMG]http://i42.tinypic.com/vif7ki.png[/IMG]

Here's what I want to know how to do...tell me how possible this is?

I want to move sda6 (Grub) to the front, move sda7 to the second spot after sda6, sda8 next, then sda4, and then combine sda1 and the unallocated portion at the very end.

My main goal is to have sda1 and unallocated to be joined to create a large shared folder for my Ubuntu and Windows 7. Is this possible?

---

### Post by wolfen69 on 2012-01-26
I think this may be difficult. You may want to consider just formatting the unallocated partition to ntfs and use it as is. Ubuntu can read and write to ntfs just fine, and doesn't have a 4gb limit per file like fat32 does.

---

