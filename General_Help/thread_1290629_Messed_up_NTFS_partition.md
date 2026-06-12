---
title: "Messed up NTFS partition"
date: 2009-10-13
forum: General Help
---

### Post by BeardedLinuxGeek on 2009-10-13
I can't boot into windows, I get a BSOD real fast and then it shuts down.

I tried mounting the drive in ubuntu and got the error message:
```

ntfs_attr_pread: ntfs_pread failed: Input/output error.
Failed to read NTFS $Bitmap: Input/output error

```

So I tried booting into UBCD4Win (a windows XP live CD) and it couldn't run a chkdsk, kept saying the partition wasn't formatted

I tried running ntfsfix from ubuntu and that failed.

Normally I would assume it was just beyond repair, but I booted into SystemRescueCD (based on gentoo I believe). I was able to mount the drive with just the simple command "mount /dev/sda1 /mnt/sda1". That worked perfectly, I could look around the drive, see all my files etc. The problem then was backing them up. I tried plugging in an external harddrive and "fdisk -l" wouldn't even see the drive. I tried enabling networking so i could backup over the network, but I couldn't get that working either.

I was going to post over at SRCD to figure out how to get networking up and running, but then I figured, why couldn't ubuntu mount the harddrive? Maybe some sort of security thing that SRCD does have? Any idea to get this drive mounted on Ubuntu? (I also tried knoppix, and that wouldn't mount it either - same error message).

---

### Post by lidex on 2009-10-13
Not my area of expertise but have you tried all your options from within windows, ie: booting in safe mode, repair option booting from windows disk?

---

### Post by BeardedLinuxGeek on 2009-10-15
Yea, I tired all that. I'm really confused why ubuntu can't mount the drive but gentoo can, even when I'm using the same command on both operating systems.

---

### Post by rhythmiccycle on 2009-10-15
i had a hard drive that wouldn't mount and running

```
fsck
```

on it while it was unmonuted worked

you also might want to look into

```
ddrescue
```

it used for rescuing messed up HD's (you need to install it first), but you need free space on another HD that is bigger than the HD you are rescuing.

from the way you write, I think you can figure out how to use these, but let me know If you need help with either of those commands.

---

### Post by lidex on 2009-10-15
Check out this post
[http://www.linuxforums.org/forum/misc/143402-recovering-data-external-hard-drive.html]("http://www.linuxforums.org/forum/misc/143402-recovering-data-external-hard-drive.html")

#7 & #8 specifically

Useful tools:
[ultimate boot cd]("http://www.ultimatebootcd.com/")

[ubcd for windows]("http://www.ubcd4win.com/")

---

### Post by superdav42 on 2009-10-15
I believe the reason that sysrescuecd is able to mount it is because it uses the ntfs driver while ubuntu uses ntfs-3g driver by default. In this case the ntfs is read only which might let it mount it even though it is really messed up. I would try ```
mount -t ntfs /dev/sda1 /mnt/sda1
``` or
```
mount -t ntfs -o ro,force /dev/sda1 /mnt/sda1 
```
also look at the output of dmesg for more detailed error after trying to mount. It might give you a better idea of what is going on.

---

### Post by ChrisWebb on 2009-10-26
If the $Bitmap is corrupt then it's probably a bad sector. HDD Regenerator is good for that sort of thing, but it costs money. Still, it brings hard drives back to life, and it would be silly to throw away a drive over 1 bad sector.

[http://www.dposoft.net/](http://www.dposoft.net/)

Thinking about it, I seem to remember that the trial version will recover 1 bad sector and then stop. That might be all you need...

Hope that helps someone.

---

### Post by az on 2009-10-26
> **ChrisWebb said:**
> If the $Bitmap is corrupt then it's probably a bad sector. HDD Regenerator is good for that sort of thing, but it costs money. Still, it brings hard drives back to life, and it would be silly to throw away a drive over 1 bad sector.

[http://www.dposoft.net/](http://www.dposoft.net/)

Thinking about it, I seem to remember that the trial version will recover 1 bad sector and then stop. That might be all you need...

Hope that helps someone.

I strongly suggest you image the drive before trying to fix it in any way.  Use Gnu ddrescue as suggested:

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

If it was a bad block that caused the problem, the problem will be solved and you will be able to mount the image.  If the problem is that the  filesystem is corrupt, then you may be able to repair the filesystem:

[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

If that fails, then you can use file-carving software to recover most of your data from the image.

---

