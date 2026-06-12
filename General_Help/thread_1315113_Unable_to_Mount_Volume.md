---
title: "Unable to Mount Volume"
date: 2009-11-05
forum: General Help
---

### Post by rjwilsonster on 2009-11-05
Long story short, I installed xubuntu 9.1 the other day. Everything was working fine, then today I restarted and my partition (sda 6) is missing. It's present on gparted, but I can't mount it. Any suggestions?

---

### Post by john.nicholls on 2009-11-05
Is it in /etc/fstab? How are you trying to mount it?

---

### Post by kedarm on 2009-11-05
> **rjwilsonster said:**
> Long story short, I installed xubuntu 9.1 the other day. Everything was working fine, then today I restarted and my partition (sda 6) is missing. It's present on gparted, but I can't mount it. Any suggestions?

Have you tried mounting it from the command line? Try this -
```
$~ mkdir temp
$~ sudo mount /dev/sda6 -t X temp/
```
Here, X = vfat if sda6 is a FAT32 partition
or X = ext2/3 if sda6 is a ext2/3 partition
(you could find out what sort of partition it is from gparted)

If the drive itself has not got corrupted, you can browse the files through the command line in the temp directory.

If the drive is fine, you could add the following line to your /etc/fstab file -
```
/dev/sda6 /media/temp vfat auto,users,rw 0 0
```
(the above will mount the partition to /media/temp)

On your next restart, the drive should get mounted automatically. You could also try -
> ~$ sudo mount -a
to mount it immediately (if you're in a hurry).

HTH

---

### Post by rjwilsonster on 2009-11-05
I'm not sure how this happened, but the mount point apparently changed. I found the volume... it's just not where I left it. :P Thank everyone for their help, though. As of now, it's just going to take a bit of reorganizing.

---

