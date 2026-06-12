---
title: "imaging problem with ddrescue"
date: 2011-02-23
forum: General Help
---

### Post by s8472 on 2011-02-23
Hi everyone,

I tried this in "General Help>To dd or ddrescue" thread a week ago but got no answers.  I am thinking nobody follows the thread any more.  I also searched General Help with "ddrescue" and been through several threads I thought relevant to no avail. So here goes:

I am trying to take an image of the 100GB ext4 root partition of my Lucid AMD64 install.  Clonezilla ends up with "Something went wrong...", I think because it still lacks ext4 support.  So I boot up with SystemRescueCD 2.0 and, after filling up the empty space on the partition with zeroes, I do this:

```
mkdir /mnt/bckup
mount /dev/sdb1 /mnt/bckup
ddrescue /dev/sda3 /mnt/bckup | bzip2 -z -7 > /mnt/bckup/root-img.bz2

```

However, all I get is this error message:
```
ddrescue: both input and output files must be specified.  Try ddrescue --help
```

I have been through the man/info pages several times, but the solution still eludes me.  dd works and finally I did the job with it, however, any pointers in the right direction, or light as to the matter of this error would be much appreciated.

Thanks in advance.

---

