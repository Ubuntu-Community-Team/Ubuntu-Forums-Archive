---
title: "Partitions for Swap"
date: 2012-10-05
forum: General Help
---

### Post by josephmills on 2012-10-05
I have a question about partitioning. Here is a drive that I have 



[IMG]http://imagebin.org/231037[/IMG] 


 I am wondering if I can remove the swap that is in sda6  and make  the unallocated section bigger then make that my swap ?  is this possible ? Sorry for the n00bish question I just have never really got into partitioning. Thanks for your time and I look forward to hearing from you in the future.

---

### Post by oldfred on 2012-10-05
I am not sure you gain much of anything. The unallocated is just over 1MiB not GiB. With the new 4K drives & SSDs, partitions are rounded at 1K and that often leaves some more unallocated. You might from liveCD and with swapoff just be able to expand the current swap.

If you delete & recreate swap, you will have to update fstab with new UUID.

---

### Post by josephmills on 2012-10-05
> **oldfred said:**
> 
If you delete & recreate swap, you will have to update fstab with new UUID.

Why Did I have the feeling that you where going to answer this :)
Thanks a bunch 

Joseph

---

