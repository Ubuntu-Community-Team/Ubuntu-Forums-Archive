---
title: "fstab entry for 2nd disk fails to mount - can't see any error"
date: 2011-03-15
forum: General Help
---

### Post by XEtedBear on 2011-03-15
One entry I have put in fstab results in the failure of a partition to be mounted at boot time. I get the message:
```

The disk drive for /media/WinXP is not ready yet or not present.

Continue to wait; or Press S to skip mounting or M for manual recovery

```

If I choose M and enter the command:
```
mount -t ntfs /dev/sdb1 /media/WinXP
```
then I get no error message, but the partition still doesn't seem to be mounted, when boot completes. 

I don't understand this failure.

I have created my fstab file using UUIDs to boot Ubuntu on my dual boot machine. It works fine, booting from the hard-disk which is Master on my Secondary IDE channel. For Ubuntu booting the MBR and grub menu are on this disk. The default is to boot Ubuntu , but with an option to select Windows Xp.

As an aside, I can set an option in my BIOS to make the Master disk on the Primary IDE channel the first disk, rather than the second disk. Then the system boots from the MBR on this Primary IDE channel and boots only to WinXP. That works fine.

When running Ubuntu I use space on the Windows disk (on the Primary IDE channel) to hold backups of key Ubuntu files in case I loose Ubuntu - as I did for the past few days. So, to mount this partition I inserted this line into my fstab:
```
UUID=0e4851c44851ab6b	/media/WinXP	ntfs	nosuid, nodev, allow_other	0	0
```

I know the UUID is correct because I have checked it with blkid. But the partition is not mounted at boot time. I don't even get an icon for the partition on my desk top. It appears in the 'places' menu, as unmounted, but mounts as soon as I click on it. However, this causes some of my linux apps, which want to load and save to this partition, to post an error message until I have manually mounted it via clicking on it in the Places menu.

I want to avoid this manual step by having the partition automatically loaded at boot time. What am I doing wrong?

---

### Post by Morbius1 on 2011-03-15
You have syntax errors ( spaces, etc .. ) in your fstab line. Try this instead:

Unmount the partition if you mounted it manually:
```
sudo umount /media/WinXP
```Change the line in fstab to this:
```
 UUID=0e4851c44851ab6b /media/WinXP ntfs defaults 0 0
```Then run the following command to test for errors and mount it again:
```
sudo mount -a
```

---

### Post by XEtedBear on 2011-03-15
Thanks for the advice - I thought that fstab was sort of free form. Now I understand that it probably had tab characters as well as multiple spaces in it. However, having made the changes you suggest, the result is:
```

tony@Advent:~$ sudo mount -a
ntfs-3g: Failed to access volume 'UUID=0e4851c44851ab6b': No such file or directory

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org

```

Is this because the type should be ntfs-3g, rather than ntfs? I suspect not, on the basis that mount cannot find the entity with that UUID. The UUID is correct, according to blkid

---

### Post by Morbius1 on 2011-03-15
(1) In ubuntu ntfs = ntfs-3g

(2) Post the output of the following command to check the uuid number:
```
sudo blkid -c /dev/null
```

---

### Post by XEtedBear on 2011-03-15
```

tony@Advent:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="WinXP" UUID="0E4851C44851AB6B" TYPE="ntfs" 
/dev/sdb1: LABEL="Paging" UUID="F044F53544F4FEE2" TYPE="ntfs" 
/dev/sdb5: UUID="f791d3de-1702-49d4-bd57-caa720429c86" TYPE="ext4" 
/dev/sdb6: UUID="b20e987e-0947-4c48-a23e-5c299655c653" TYPE="swap" 
/dev/sdb7: UUID="4ecb88aa-6970-450a-bcb4-719da6eddb88" TYPE="ext4"

```

---

### Post by XEtedBear on 2011-03-15
Further more, I can 'sudo umount /media/WinXP', but I cannot do the reverse:
```

tony@Advent:~$ sudo mount /dev/sdb1 /media/WinXP
fuse: failed to access mountpoint /media/WinXP: No such file or directory

```

---

### Post by Morbius1 on 2011-03-15
There's your answer:
>  /dev/sda1: LABEL="WinXP" UUID="0E4851C44851AB6B" TYPE="ntfs"[COLOR=Blue]0E4851C44851AB6B[/COLOR]
not
[COLOR=Blue]0e4851c44851ab6b

[COLOR=Black]You know how picky Linux can be with caps[/COLOR]. 
[/COLOR]

---

### Post by XEtedBear on 2011-03-15
> **Morbius1 said:**
> There's your answer:
[COLOR=Blue]0E4851C44851AB6B[/COLOR]
not
[COLOR=Blue]0e4851c44851ab6b



Sorry, tried that; makes no difference

---

### Post by Morbius1 on 2011-03-15
Is the disk damaged? Can you boot into WinXP?

---

### Post by XEtedBear on 2011-03-15
With respect to the immediate previous post from me: the value of that post was somewhat less than that of a pinch of goat droppings.

I'll remember to have caps lock on  - but only when editing fstab, and then only for certain disks!

Linux: never a dull (or consistent) moment.....

---

