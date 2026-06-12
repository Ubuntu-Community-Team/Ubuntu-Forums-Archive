---
title: "Need help with external hard drive"
date: 2009-08-13
forum: General Help
---

### Post by BrownTown6 on 2009-08-13
I have a 200 Gb hard drive that i put in the 3.5" external data storage enclosure model number nsp-hd-343-u2s. I used the drive when i first started using ubuntu and had no problems with it but then after formatting it I no longer have permission to alter it. It says that I'm not the owner. I'm running ubuntu 9.04 if that helps. Also I have tried formatting it to ext2, ext3, and ext4.

---

### Post by P4man on 2009-08-13
take ownership of the drive again :)

```
sudo chown -R username:username /yourdisk
```

eg:

sudo chown -R BrownTown:BrownTown /media/disk-2

---

### Post by BrownTown6 on 2009-08-13
Thank you for that but now I'm having a different problem. no matter what format i put in always say "The permissions of 'disk' could not be determined" I have tried the same formats as before and they all say this.

---

### Post by tgeer43 on 2009-08-13
> **BrownTown6 said:**
> Thank you for that but now I'm having a different problem. no matter what format i put in always say "The permissions of 'disk' could not be determined" I have tried the same formats as before and they all say this.Did you take ownership of the drive as P4Man advised in post #2? When you say "no matter what format i put in" are you talking about reformatting to different filesystems such as ext2, ext3, etc.? If you are then be aware that every time you reformat with gparted, you are doing so as root and therefore root will once again have ownership of the drive so you'll have to take it back again with chown. Once you are the owner, you should no longer see "The permissions of 'disk' could not be determined" and the info in the permissions tab should not be greyed out anymore.

tgeer

---

### Post by BrownTown6 on 2009-08-13
ok. I did what was said in post number 2 and it still says im not the owner.

---

### Post by P4man on 2009-08-14
you probably did it in in the wrong place. Can you paste the output of "mount" ?

---

### Post by BrownTown6 on 2009-08-14
Sorry. I don't know if I just had to restart the hard drive or what but it shows I'm the owner now. Thanks for help Both of you.

---

