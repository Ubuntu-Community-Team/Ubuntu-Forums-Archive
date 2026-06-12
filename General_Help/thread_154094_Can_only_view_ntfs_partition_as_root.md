---
title: "Can only view ntfs partition as root"
date: 2006-04-02
forum: General Help
---

### Post by f3tus on 2006-04-02
This is the ntfs drive in fstab:
```
/dev/sda1       /media/sda1     ntfs    nls=utf8,umask=0222     0       0
```
I guess this should let me view the partition as a normal user, but I can only view it as root.

The only reason why I want to access it, is to create a link to my music folder in Windows, that way I won't have to copy all the stuff and it really isn't worth running as root lol.

I tried all sorts of options in the fstab, rebooted like 10 times, but I can never access the damn drive (except in root)!

What seems to be the matter here?

Thanks.

---

### Post by joft on 2006-04-02
Hi,

I use the mount options uid and gid in fstab to explicitly "turn" the files over to my user. So you could try:

```
nls=utf8,umask=0222,uid=<username>
```

or even:

```
nls=utf8,umask=0222,uid=<username>,gid=<groupname>
```

(Your username without the "<" and ">", of course).

---

### Post by f3tus on 2006-04-02
No, that didn't work :/ Thanks anyway.

Anyone else?

---

### Post by Bekker on 2006-04-03
The only thing I can tell you is that this works for me
```
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222,auto        0       0
```
I've also had troubles mounting ntfs, with this line I can mount 'm. But I don't think the "auto" option will make a difference...
Did you make your /media/sda1 world readable?

---

### Post by f3tus on 2006-04-03
What exactly do you mean?

Anyway, this is how it looked before
```

/dev/sda1   /media/sda1   ntfs   uid=500,gid=500,umask=000,exec,dev,rw 1 0
```

And it worked...

I formatted the ntfs disk and re-installed Windows on it, I also re-installed the grub bootloader on my reiserfs disk, since then it doesn't work lol.

My current uid and gid for my user are 1000, as you can see, it was set to 500, could it have changed to 1000 somehow? Nobody is 500 ATM :P

---

### Post by aysiu on 2006-04-03
Try mounting to a static directory like /windows instead of a /media directory. Sometimes that makes a difference.

---

### Post by mikkelwe on 2006-04-03
Broken perms on /dev/sda could screw things up. What does ls -l /dev/sda say?

---

### Post by mikkelwe on 2006-04-03
Oh yes, and what does ls -l /media/windows and ls -ld /media/windows or whatever 
the mount point was say, after it's mounted?

---

### Post by f3tus on 2006-04-04
```

ls -l /dev/sda1
brw-rw----  1 root disk 8, 1 2006-04-04 10:22 /dev/sda1

ls -l /media/sda1
ls: /media/sda1: Permission denied

s -ld /media/sda1
dr-x------  1 root root 8192 2006-04-03 22:34 /media/sda1

```

---

### Post by Blutack on 2006-04-06
I had the same issue - for music too...
The solution is in system settings, Hard Disks.  I can't remember exactly what I did but I had to go admin mode and then set accessible.  It was dead easy but i guess the GUI config tool messes up the manual way cos I tried manually for ages..
Hope this helps

---

### Post by f3tus on 2006-04-06
No that didn't help :/

Anyway, I copied an .iso image as root from the windows disk, and placed it onto my user's desktop, but I can't burn it without being root. Is this normal? Basically every file I copy as root, can only be used as root... Maybe that's the problem, because I mount the drive as root?

---

