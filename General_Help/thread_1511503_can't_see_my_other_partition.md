---
title: "can't see my other partition"
date: 2010-06-16
forum: General Help
---

### Post by spikehay on 2010-06-16
I just installed Xubuntu on my eeePC 901 netbook. I was using Ubuntu 10.04. I have two partitions on my SSD: a 4 gig that the OS is on, and a separate 8 gig. I can't see or mount the 8 gig. It worked fine before when I was using straight Ubuntu.

Any ideas? 

Thanks,

Mike

---

### Post by cariboo on 2010-06-16
What's the output of:

```
sudo fdisk -l
```

---

### Post by spikehay on 2010-06-16
> **cariboo907 said:**
> What's the output of:

```
sudo fdisk -l
```

Oh, so you have to do sudo. I wasn't getting any output. It turns out the partition is NTFS, which I didn't know (I got this computer from somebody else). I added a line to FSTAB and it mounts now.

Thanks!

---

