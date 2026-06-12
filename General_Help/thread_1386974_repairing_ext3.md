---
title: "repairing ext3"
date: 2010-01-21
forum: General Help
---

### Post by bonfire89 on 2010-01-21
Hello,

The last time I ran 
```
efsck -yvf /dev/vg0/lv0
```

I receive the error
```
e2fsck: Can't allocate duplicate block header

e2fsck: aborted
```

before that, I had receive similar messages about inodes and such. Prior to my most recent attempt at running e2fsck I shuffled around some sata cables in case maybe there was a bad port on one of my sata controllers.

The data on the LV seems be fine aside from the errors that I am getting with e2fsck.



extra info:

The reason why I am running this is because I want to reduce the size of the LVM and e2fsck is a prerequisite to resize2fs.

I am shrinking the size of the LVM because my ultimate goal is to dismatle the LVM into independant physical hard drives.

so... I bought an extra HD... and so.. Copy from the LVM to the free drive, reduce LVM, remove drive from LVM, copy to new free hard drive etc.




what are my options?




Thank you very much. I have been struggling with this for quite some time now, and I could potentially lose a lot of data.

I know one option is to buy more hard drives.... but... I don't really have the money for that =/


Thanks again.

---

### Post by bonfire89 on 2010-01-30
I borrowed some hard drives, offloading all the data temporarily


problem abandoned

---

