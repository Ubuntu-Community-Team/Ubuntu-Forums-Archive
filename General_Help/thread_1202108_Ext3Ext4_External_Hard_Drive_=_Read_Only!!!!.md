---
title: "Ext3/Ext4 External Hard Drive = Read Only!!!!"
date: 2009-07-01
forum: General Help
---

### Post by zacharyrs on 2009-07-01
How can I make my ext3/ext4 external hard drive have full permissions so that I can write and edit it? Pretty Please?

If you can fix this I will put a photo of you on my desktop and defend your name against nay-sayers.

---

### Post by geirha on 2009-07-01
Alt+F2 -> gksu nautilus

In the nautilus window you get (which has root privileges), browse to where the disk is mounted. Typically under Filesystem -> media. Right click the folder -> Properties -> Permissions tab. Change ownership from root to your user.

---

### Post by colau on 2009-07-01
> **zacharyrs said:**
> How can I make my ext3/ext4 external hard drive have full permissions so that I can write and edit it? Pretty Please?

If you can fix this I will put a photo of you on my desktop and defend your name against nay-sayers.
```

gksudo nautilus

```

---

### Post by zacharyrs on 2009-07-01
Geirha: You are a genius, and when someone says that you are not please direct them to me and we will escalate the matter further.

Now I am able to create directories and so on only in the folder which came on the hard drive once I formatted/partitioned in Ubuntu. See screenshot. Is it normal for Ubuntu to create a folder for me to put stuff in? I ask because I can't make any folders or save anything UNLESS I am in that specific folder. Seems odd to me, craving your genius and higher level insight.

---

### Post by geirha on 2009-07-01
No the lost+found folder should not be touched, it is used by the filesystem, and should only be accessible to root. If you changed the ownership of the lost+found folder, change it back. You want to change the root of the external drive, which judging from your screenshot is /media/ex_hd

---

