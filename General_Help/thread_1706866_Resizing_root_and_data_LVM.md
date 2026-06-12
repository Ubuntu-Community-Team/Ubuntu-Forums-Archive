---
title: "Resizing root and data LVM"
date: 2011-03-14
forum: General Help
---

### Post by flycast on 2011-03-14
I have an eBox server which I believe is based on ubuntu. When it installed there was a root, swap and a home partition. They are ext4 file systems. My root is too small and I need to resize it. Unfortunately, there is no extra space.

I need to downsize the home partition by 10G and then upsize the root by 10G. All I can find are tutorials on upsizing partitions that assume that you have extra drive space.

My thought is:
[LIST=1]
[*]boot from live CD
[*]downsize the home file system
[*]downsize the home volume
[*]upside the root volume
[*]upsize the root file system
[/LIST]

Does this seem right? The key is how do I downsize the home file system and partition?

---

