---
title: "Write to hfs+ from non-root user"
date: 2009-08-07
forum: General Help
---

### Post by somethingkindawierd on 2009-08-07
I first want to preface this with a note that I HAVE searched these forums and found alot on getting hfs+ volumes mounted. I can mount mine, and I can write to it via the root user.

But what I cannot do is write to it from my normal user. I have tried everything I know of, and everything I've found here in the forums, and can still only write via sudo...

So does anyone know what I need to do with my fstab command to give my normal user access to the hfs+ volume?

Here is my current fstab:

```
/dev/sda3 /mnt/common hfsplus defaults,uid=1000,gid=1000 0 0 
```I have also tried:
```
/dev/sda3 /mnt/common hfsplus defaults 0 0 
/dev/sda3 /mnt/common     hfsplus defaults,user,noauto     0       0 
/dev/sda3 /mnt/common     hfsplus defaults,user,auto     0       0
```None of these give my normal user access.

---

