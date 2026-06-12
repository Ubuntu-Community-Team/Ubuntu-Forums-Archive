---
title: "Problem with hard disc when i use linux!!!"
date: 2011-05-22
forum: General Help
---

### Post by masterserver on 2011-05-22
Hi to all. I have windows 7 and ubuntu 11.04 installed on my system on the same hard disc (500GB Windows partition NTFS, Linux Partition ext4) in two different partitions. I have an extra hard disc (600GB NTFS) only for data. When i use ubuntu and then use windows, i cannot open some  files (from Windows) in the second disc. I must restart the windows, let the windows check the second disc and restore the corrupted files. If use linux again and then use windows and try to open some file in the second disc i have the same problem again and i must do the same procedure. 

Do you have any idea what is going on?

Thanks

---

### Post by kd7swh on 2011-05-22
This is a pretty typical problem. Windows doesn't expect the file system to change between boots.

This stinks, but I don't know if there is much that can be done.

You can make sure that the drives cleanly mount and unmount. (Make sure to shutdown Linux properly.)  

Maybe using tools like ntfs-config could help but really this is Microsoft's fault.

---

