---
title: "is tmp directory writable while rootfs is full"
date: 2012-06-09
forum: General Help
---

### Post by vkaushal21 on 2012-06-09
Can i use tmp directory to hold small temporary files while rootfs is non writable (i have large enough page cache/ memory)

I am writing an application on a system where rootfs sometimes becomes non writable due to various reasons, and i want some important threads (which must write a file), to continue running. i came to know that /tmp is generally writable even if rootfs becomes full (no space on disk). is it true? 

I tried searching online, but could not find any references to the same, can somebody point me to the same. 

Thanks

---

### Post by CharlesA on 2012-06-09
Have you found out why / is full ?

---

### Post by Cheesemill on 2012-06-09
It all depends on where /tmp is mounted. If it's on the same filesystem as / then it won't be writeable as the filesystem is full. If it's mounted on a different partition (or RAM disk) then it should be writeable.

If a process is running as root then it will be able to write *some* files even in the first situation due to 5% of an ext partition being reserved for just this reason.

---

