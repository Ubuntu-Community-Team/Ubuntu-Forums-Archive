---
title: "Resume issues"
date: 2010-04-13
forum: General Help
---

### Post by benekastah on 2010-04-13
So I'm having this weird problem where my computer wants to continuously resume a session from hibernate no matter how I shut it down. I think it started when I tried to hibernate my computer with the battery really low. Somehow it messed it up. In any case, it can't resume properly, but gets stuck somewhere in the middle (I think when it's trying to sort out the resume image). Each time I power it on I have to boot it, restart in the middle of the boot so the boot menu comes up as it starts up again, edit commands before boot and add the "noresume" option so it will boot up normally. Is there any way for me to permanently fix this instead of having to manually fix it each time? Thanks!

---

### Post by plucky on 2010-04-13
> **benekastah said:**
> So I'm having this weird problem where my computer wants to continuously resume a session from hibernate no matter how I shut it down. I think it started when I tried to hibernate my computer with the battery really low. Somehow it messed it up. In any case, it can't resume properly, but gets stuck somewhere in the middle (I think when it's trying to sort out the resume image). Each time I power it on I have to boot it, restart in the middle of the boot so the boot menu comes up as it starts up again, edit commands before boot and add the "noresume" option so it will boot up normally. Is there any way for me to permanently fix this instead of having to manually fix it each time? Thanks!

You could try turning the swap off to see if that clears out the swap partition,where I think the resume file should reside.
If that doesn't work,then you would have to delete the swap partition and re-create it again just to get rid of the resume image.

Please post output from a terminal of ```
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

Good Luck

---

### Post by benekastah on 2010-04-14
Here is the terminal output.

For cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1afdc170-0547-457e-b17f-cc4bd749d088 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=d4c5337b-0547-41e7-8f3f-4ab9a61029a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

For cat /etc/initramfs-tools/conf.d/resume:
```
RESUME=UUID=d4c5337b-0547-41e7-8f3f-4ab9a61029a5
```

I tried dumping my swap, and that is indeed where the resume image should be (according to my research). It still didn't fix the problem though. I have had an error message while booting ever since loading this system that says something like, "One of the drives in /etc/fstab cannot be mounted and it cites /dev/mapper/cryptswap1 as the culprit. It has never given me trouble before, but it may be related. I've been considering getting rid of my swap partition and just creating a swap file. Would that help? Any other ideas?

---

