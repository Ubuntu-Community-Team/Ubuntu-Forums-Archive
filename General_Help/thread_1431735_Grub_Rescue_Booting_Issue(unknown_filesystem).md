---
title: "Grub Rescue Booting Issue(unknown filesystem)"
date: 2010-03-17
forum: General Help
---

### Post by PBK1999 on 2010-03-17
I am at college and am trying to help my girlfriend work out her problem with my netbook back at home. She isn't that exactly computer savvy and she has somehow managed to screw up the booting process. My netbook is dual boot with XP and Ubuntu's latest version and she wanted to use XP instead of Unbuntu, something happened that scared her so she decided to shut off the computer as it was rebooting I guess. Now there is a grub rescue prompt with the follow when she starts the computer...

```
GRUB loading.
error: no such partition
grub rescue>
```I have been doing my research on it, because I am relatively new to Linux myself(decided to get it myself because I use it in my classes), but to no avail have I gotten anywhere.

I have tried talking to her on the phone with a few trials by trying multiple approaches that I have found on various sites. All of them did not work. For example I used "set prefix=(hd0,1)" and then tried to boot but constantly get the message "error: unknown filesystem"

Any ideas? They would be greatly appreciated.

---

### Post by mikewhatever on 2010-03-17
I can well be a file system or partition related problem. Running <sudo fdisk -l> from the live cd might through some revealing error. If that's the case, <sudo fsck -Ay>, also from the live cd might help.

---

### Post by PBK1999 on 2010-03-17
There is no optic drive. Is the only way to fix this by booting off of a flash drive? I'd like to find an alternative.

---

### Post by lordskid on 2010-03-17
at the rescue prompt try to type ls see if it works.

that is an L not an I.

---

### Post by mikewhatever on 2010-03-17
> **PBK1999 said:**
> There is no optic drive. Is the only way to fix this by booting off of a flash drive? I'd like to find an alternative.

Booting from an external device is the way, if it is the file system issue. I don't see an alternative, neither to troubleshooting, nor to fixing, since the system wouldn't even pass the boot screen.

---

### Post by john newbuntu on 2010-03-17
Follow step 15 from the post below.  As lordskid suggested, "ls" should give you the partitions.  Then you would do an "ls" on each individual partition to determine your boot partition.  Example:
ls (hd0,5)/

If this gives /boot, then your X is 0 and Y is 5.  Follow the remaining steps from this post.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by PBK1999 on 2010-03-18
I have tried the ls command and I got an error that says "unknown filesystem" or something along those lines. I will be able to get my hands on the machine on saturday so I will try all of these things and will let you know what works. But more ideas are still welcome!

---

