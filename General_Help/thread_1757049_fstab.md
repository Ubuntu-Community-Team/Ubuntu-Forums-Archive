---
title: "fstab"
date: 2011-05-13
forum: General Help
---

### Post by shashanksingh on 2011-05-13
I have appended the following line in  fstab to auto-mount my ntfs partition on startup.

/dev/sdb2       /media/Jupiter          ntfs-3g        users,rw,exec,auto       0 	0

A problem occurs when I unmount it and then when I click on "Jupiter" in places to remount. It shows the following error.

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

---

### Post by Nerotriple6 on 2011-05-13
Did you try mounting it in Terminal as root?

You could also try editing your fstab, I have my music drive as NTFS and this line works fine for me.

```
/dev/sdc1 /home/nero/Musikk ntfs-3g defaults,force 0 0
```

---

### Post by mikewhatever on 2011-05-13
If you need to mount and unmount a partition by clicking it, don't add it to fstab. On the other hand, if you want a partition mounted permanently, that's what fstab is for.

---

### Post by shashanksingh on 2011-05-13
> **Nerotriple6 said:**
> Did you try mounting it in Terminal as root?

You could also try editing your fstab, I have my music drive as NTFS and this line works fine for me.

```
/dev/sdc1 /home/nero/Musikk ntfs-3g defaults,force 0 0
```

Yes, it does mount from the terminal as root.
Apparently I do not have privileges as per that line.

Btw, what does "force" in that line do?? Coz that is the only diff I think

---

### Post by shashanksingh on 2011-05-13
> **mikewhatever said:**
> If you need to mount and unmount a partition by clicking it, don't add it to fstab. On the other hand, if you want a partition mounted permanently, that's what fstab is for.

Hmm. Is there another option using which I can auto-mount a drive??

I want to auto-mount it coz it generally has the documents Im working on and my workspace, which is used by default by some apps like eclipse

---

### Post by mikewhatever on 2011-05-15
Actually, yes, you can use udisks:

```
udisks --mount /dev/sdc1
```

You can also use UUIDs instead of /dev/sdXY, and to list all available devices, try
 **udisks --enumerate-device-files**.
Now, to automount, add the command to your session startups.

---

