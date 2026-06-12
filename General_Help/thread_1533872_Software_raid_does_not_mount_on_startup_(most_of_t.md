---
title: "Software raid does not mount on startup (most of the time)"
date: 2010-07-18
forum: General Help
---

### Post by R4KFFE on 2010-07-18
I am running 64bit ubuntu 10.04. I have an nvidia software raid formatted with ntfs. The raid only mounts about every 10-15 boots. It is completely random on when it will mount. I even have included "force" in the ntfs-3g mount options.

Also, possibly related, many times ubuntu will not even load unless I load windows first and then restart. I run Ubuntu on its own partition using ext3, so this makes no sense.... It makes me scared to run a computer with only Ubuntu because it seems Ubuntu cannot load unless window loads before it! I could understand this if Ubuntu was formatted as NTFS, but the only NTFS drive Ubuntu sees is the raid, which is not mounting anyways, so why is it dropping to the command prompt?

Does anyone have any insights into this?

---

### Post by R4KFFE on 2010-07-18
Does anyone have any ideas?

---

### Post by R4KFFE on 2010-07-19
Come on. Someone has to have an idea.

---

### Post by kaelspencer on 2010-07-19
I'm not sure what you mean by "nvidia software raid formatted with ntfs". If it is a software RAID and formatted with NTFS, I imagine it is for Windows. What steps did you take to get it recognized under Ubuntu?

---

### Post by R4KFFE on 2010-07-20
I don't think I took any steps. It was auto-recognized under ubuntu. I just had to add a line to fstab:

```
/dev/mapper/nvidia_ajccdfcd       /media/raid   ntfs-3g       user,force,nosuid,exec,utf8,fmask=0111,dmask=0000      0         0
```

Ubuntu 9.10 had no problem mounting the raid. Ubuntu 10.04 will mount it but only 5% of the time. Is there a log file I can look at?

---

### Post by R4KFFE on 2010-07-20
Btw, when Ubuntu 10.04 boots it will tell me that /media/raid is not mounting and to press s to skip mount or continue to wait. I can wait forever and it will never complete mounting.

---

