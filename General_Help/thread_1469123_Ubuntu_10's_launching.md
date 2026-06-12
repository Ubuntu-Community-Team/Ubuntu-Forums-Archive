---
title: "Ubuntu 10's launching"
date: 2010-05-01
forum: General Help
---

### Post by huangyingw on 2010-05-01
Hello, I always met these issues on Ubuntu 10.4.
Sometimes when launching, there would always a screen saying that it is checking drive for error. And indeed, this process takes a long time.
And what is more curious is that: during the process of checking drive, I saw no hard disk lamp flash. So, this indicate that in fact Ubuntu is not checking
 hard disk. Am I right?
 How could I disable the check when booting. It would take a long time.
 And, if I update the /etc/fstab, to add a auto-mount point for a USB disk. And while booting, the USB disk is not present, or not pluged into PC, the boot
 process would hang and wait for my response. Could the boot become somehow more clever, and ignore the UBS, and continue to boot, without my attendance?

---

### Post by patagonik on 2010-05-02
I'm having the same problem here... i mean, the USB mounting error: I need to press "S" to skip this error message and continue with the boot.

---

### Post by dino99 on 2010-05-02
sudo dpkg --configure -a

[http://manpages.ubuntu.com/manpages/lucid/en/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/fsck.8.html)

---

### Post by huangyingw on 2010-05-02
> **patagonik said:**
> I'm having the same problem here... i mean, the USB mounting error: I need to press "S" to skip this error message and continue with the boot.
Comfort. The most annoying thing for me is the check drive. Even format and reinstall Ubuntu 10, will still repro this. And the time it takes becomes more and more.
I could not bear this, so I have down grade to Ubuntu 9.
Hey, do me a favor, once this two issues fixed, please let me know.
Thank in advance.

---

### Post by huangyingw on 2010-05-02
> **dino99 said:**
> sudo dpkg --configure -a

[http://manpages.ubuntu.com/manpages/lucid/en/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/fsck.8.html)
Will this command help?

---

### Post by anchois on 2010-05-03
For the annoying "S" to skip the mount of drive, you just have to add "noauto" in the line of /etc/fstab corresponding to the device.
I upgraded from Hardy to Lucid, and it seems that the upgrade remove this parameter that I had already.

If someone know what replace the checkfs script, I'll be really greatfull as I'm searching to optimize boot time and fsck take forever to check my vfat partition.

Thanks,

Rgds,
F.

---

### Post by huangyingw on 2010-05-12
> **anchois said:**
> For the annoying "S" to skip the mount of drive, you just have to add "noauto" in the line of /etc/fstab corresponding to the device.
I upgraded from Hardy to Lucid, and it seems that the upgrade remove this parameter that I had already.

If someone know what replace the checkfs script, I'll be really greatfull as I'm searching to optimize boot time and fsck take forever to check my vfat partition.

Thanks,

Rgds,
F.
I think the "noauto" is meanless. 
While the worse is the checkfs at launching. It took more and more time with every launching. That is the reason that I retrace back to Ubuntu 9.10:(

---

