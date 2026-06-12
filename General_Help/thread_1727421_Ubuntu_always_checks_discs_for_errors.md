---
title: "Ubuntu always checks discs for errors"
date: 2011-04-12
forum: General Help
---

### Post by cblnchat on 2011-04-12
I was just wondering why Ubuntu is always checking my discs for errors.  This happens every few times i turn the computer off and back on.  Maybe every 2 or 3 times.  Is this just ubuntu checking the discs or something to worry about?

Thanks

---

### Post by dandnsmith on 2011-04-12
Do you shut it down, or merely power off?
Look in /etc/fstab (a text file) to see what is set for those disks, and consult the man pages for fstab to see how to interpret the results (or post them here for someone to help you)

---

### Post by cblnchat on 2011-04-12
> **dandnsmith said:**
> Do you shut it down, or merely power off?
Look in /etc/fstab (a text file) to see what is set for those disks, and consult the man pages for fstab to see how to interpret the results (or post them here for someone to help you)
I always shut it down with the button on the screen.  I rarely hold the power button and power it off.

And here is the fstab stuff
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

```

---

### Post by drs305 on 2011-04-12
You can see how often your partition is set to be checked with the following command (example is for sda5):
```
sudo tune2fs -l /dev/sda5 | grep mount
```

If the reason for the frequent checks is because of a low maximum mount count, you can change the interval (by number or mounts or by a time/date interval) using the -C or -i switches. Type "man tune2fs" for more information.

---

