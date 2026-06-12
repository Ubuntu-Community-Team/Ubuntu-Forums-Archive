---
title: "Partitioning woes"
date: 2010-12-25
forum: General Help
---

### Post by newbeeman on 2010-12-25
I am busy trying to install Ubuntu 10.10 64 bit into a "New Quad" machine with 3 drives, and am having problems sorting it all out.
When checking G Parted I find /dev/sda 1 and /dev/sdb 1 the ext4 partitions both have exclamation marks alongside them. When checking "information" it reads "No such file or directory" "Couldn't find valid filesystem superblock". The machine boots quite normally.
I have no idea what I've done wrong, but would like some help, please, especially when it also states "Some operations may be unavailable".
Finally the third drive states "unallocated". I intend to use this for my images in Ubuntu, and Video editing in a Virtualbox WinXP. How do I partition that drive?
Thanks in advance.

---

### Post by newbeeman on 2010-12-25
Bump.
I desperately need help!

---

### Post by Rubi1200 on 2010-12-25
Are all 3 drives plugged in right now?

From a LiveCD do 2 things:

post a screenshot of how GParted sees the situation.

run this command and post the output:
```
sudo parted -l
```Thanks.

---

