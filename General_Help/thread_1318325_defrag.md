---
title: "defrag"
date: 2009-11-07
forum: General Help
---

### Post by blackcloud49 on 2009-11-07
):P:lolflag: Does ubuntu come with its own defrag tool and if so where can I find it?:popcorn:

---

### Post by wojox on 2009-11-07
Ah, no. Read up on Ext4.

---

### Post by kyuubi777 on 2009-11-07
forget all you learned on micro wincrap technologies... you shan't be needing them bits of info where your going :D

---

### Post by MrDan on 2009-11-07
> **kyuubi777 said:**
> forget all you learned on micro wincrap technologies... you shan't be needing them bits of info where your going :D

I like that!  It'd be a good bumpersticker...:lolflag:

---

### Post by yo2boy on 2009-11-07
There's no need to defrag on an ext* system... :roll:

---

### Post by ivanvajar on 2009-11-07
No fragmentation on ext* - no defragmentation.

---

### Post by blackcloud49 on 2009-11-07
):P Thanks

---

### Post by calc on 2009-12-07
There is certainly fragmentation on Linux, and ext3 partitions can get extremely badly fragmented especially if you use transmission much, I know from personal experience. I have had numerous issues with downloadeds, eg Ubuntu 9.10, that are so fragmented I have to make a copy of them first to partially defrag them before I could burn them to disk, they couldn't even manage 48x cd speed (~ 7MB/s) on a drive that can do ~ 120MB/s sequential. Ext4 with prealloc is supposed to help somewhat with this issue, though I am sure it is far from perfect which is why tytso is also working on a defrag tool specifically for ext4. XFS also has a defrag tool, I'm not sure how well it works though, when I used it (8+ years ago) it ate my data.

I think the reason that the lie that Linux doesn't need to be defragged has been kept alive is due to the fact that until now only XFS has ever even had a defrag program (at least to my knowledge). This has been claimed since at least shortly after Linux was created probably because it was very hard if not impossible to write a defrag program for the older filesystems and people did not want there to be a clear public deficiency in Linux.

---

### Post by calc on 2009-12-07
You can find out how fragmented a particular file is by running filefrag (filename). Also if you are using ext4 and manage to get it fragmented, I think you can resolve this simplying by doing a cp/rm which, at least to my knowledge, should use prealloc on ex4.

---

### Post by calc on 2009-12-10
Here is a new comment by Theodore Ts'o about the status of e2defrag.

[https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22](https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22)

---

