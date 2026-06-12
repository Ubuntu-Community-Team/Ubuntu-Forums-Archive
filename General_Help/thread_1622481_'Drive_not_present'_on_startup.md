---
title: "'Drive not present' on startup"
date: 2010-11-15
forum: General Help
---

### Post by Onael on 2010-11-15
Hi. Can anyone tell me why I get this message during startup? I have to chose 'S' before I can start up my system.

"The disk drive for /data is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery"

Once upon a time I had a partition with that label, but I've since deleted it and resized my system partition to use that space. Why does my system keep looking for this drive?

Thank you.

Onael

---

### Post by sikander3786 on 2010-11-15
Hi.

Please post the output of

```
cat /etc/fstab
```

---

### Post by drs305 on 2010-11-15
and if fstab contains UUIDs:
```
sudo blkid -c /dev/null
```
although if you haven't reused the mount point it may not matter...

---

### Post by Onael on 2010-11-15
> **sikander3786 said:**
> Hi.

Please post the output of

```
cat /etc/fstab
```

```
akinci1g@akinci1g:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=17d0a406-cb92-4640-ab8b-fd26b328de56 /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=d05d941a-78b0-48c1-9c63-7b183b4fb031 /data           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=485f7634-0f14-4a53-a4fc-e078e93a2ef9 none            swap    sw              0       0
akinci1g@akinci1g:~$ 
```

---

### Post by sikander3786 on 2010-11-15
Edit /etc/fstab by

```
gksudo gedit /etc/fstab
```

Comment this line with #

```
UUID=d05d941a-78b0-48c1-9c63-7b183b4fb031 /data           ext4    defaults        0       2

```

So that it looks like

```
#UUID=d05d941a-78b0-48c1-9c63-7b183b4fb031 /data           ext4    defaults        0       2

```

Save, close and reboot to see if the error is gone.

---

### Post by Onael on 2010-11-15
That worked!! thank you. So what was going on there? How did that fix it?

---

### Post by sikander3786 on 2010-11-15
If you want to understand fstab, see this.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

There was a mount defined in your fstab for a drive that didn't exist any longer. And Ubuntu mounts all the drives defined in fstab at startup. Once you hide the mount definition for a non-existing drive (by putting #), Ubuntu doesn't read that line and therefore doesn't try to mount that one.

Happy Ubuntu-ing!

---

### Post by Onael on 2010-11-15
Cool. Makes sense. Thanks again.

---

