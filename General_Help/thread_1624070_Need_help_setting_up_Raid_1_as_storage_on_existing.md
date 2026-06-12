---
title: "Need help setting up Raid 1 as storage on existing system"
date: 2010-11-17
forum: General Help
---

### Post by nasty_fileserver on 2010-11-17
I have 10.04 installed on an 80G drive. I have 2 - 1TB drives I want to use as storage ONLY. How do I set them up as a raid 1 and share them on a Windows network?

---

### Post by Tlingit on 2010-11-17
> **nasty_fileserver said:**
> I have 10.04 installed on an 80G drive. I have 2 - 1TB drives I want to use as storage ONLY. How do I set them up as a raid 1 and share them on a Windows network?

I know what a raid is it seams simple and I have set a raid before. If you need more help then this please let me know.

[https://wiki.ubuntu.com/Raid]("https://wiki.ubuntu.com/Raid")

---

### Post by BobMUK on 2010-11-18
For the RAID array, everything you need to know is here:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

The actual create command is:
```
mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```

...but obviously use the correct devices for your 2 new drives (most likely sdb1 and sdc1, with sda1 being your existing boot device)


For windows sharing you'll need to configure Samba - FAQ here:
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

It's really quite easy and works with a minimal config file.

---

