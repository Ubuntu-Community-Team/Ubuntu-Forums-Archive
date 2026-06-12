---
title: "CD/DVD Automount"
date: 2011-07-11
forum: General Help
---

### Post by meatbiscuit on 2011-07-11
Sorry if this is a repeat, but I have been searching for hours now and this is driving me up the wall!!

When I insert a CD/DVD, it is auto-mounted in /media, but the folder beneath /media has permissions of 500.  This is a pain when sharing the drive over the network using CIFS.  Anyone know how to change the auto-mount permissions to 555?

Any help is appreciated -- this seems like a simple problem and I'm pulling my hair out over it!

P.S.  This is in Ubuntu 10.10

---

### Post by AlphaLexman on 2011-07-11
What is the result of...
```
umask
```

---

### Post by meatbiscuit on 2011-07-12
umask is 0022

---

### Post by meatbiscuit on 2011-07-12
Bump.  I can't imagine I am the only person to have this problem...ideas?

---

### Post by Surendil on 2011-07-12
```
 sudo chmod /media 555 
```

I suggest you change permissions to 660

Cheers.

---

### Post by meatbiscuit on 2011-07-13
I've tried manually changing the directory permissions (or through a script) but, even as root, It complains about the disc being a Read-only filesystem.

---

### Post by Surendil on 2011-07-13
> **meatbiscuit said:**
> I've tried manually changing the directory permissions (or through a script) but, even as root, It complains about the disc being a Read-only filesystem.

Well, actually the CD/DVD folder is only Read-Only, unless you use brasero or another burning software, you can't write on the CD/DVD.
If the problem is that other users can not access the folder, remember to change user and group ownership with commands
```
 chgpr and chown 
```
If that doesn't work, try to create a new folder anywhere you want with the access you want and change FSTAB and MTAB config so the CD/DVD is mounted on the folder you created.

---

### Post by Dscottmc7 on 2011-07-13
Somewhat the same problem...but probably worse!  I can maneuver to the cmd line but anywhere every relevant fs is "read-only."
I'm locked out...tried every cmd to change permissions...always won't even let me in and replies, "read-only!"
If it helps, I think I caused this crash by inadvertently downloading "dpkg" ...it must conflict w/ apt-get.
2nd: I wanted to mount BOTH my cdroms/dvd (Disk Utility sees them) and the only suggestion that seemed reasonable was, "Insert a blank CD into each drive and restart."
I did...and the result is I'm locked out of my U-10.04!  That machine is HP-m7674b IntelDuoCore -64, Nvidia GeForce 7300ls and running 64 Ubuntu 10.04.  (I'm on my other machine frantically searching)
If anyone can help, the answer could help us both.
Cheers,
Scott

---

### Post by meatbiscuit on 2011-07-17
> **Dscottmc7 said:**
> Somewhat the same problem...but probably worse!  I can maneuver to the cmd line but anywhere every relevant fs is "read-only."
I'm locked out...tried every cmd to change permissions...always won't even let me in and replies, "read-only!"
If it helps, I think I caused this crash by inadvertently downloading "dpkg" ...it must conflict w/ apt-get.
2nd: I wanted to mount BOTH my cdroms/dvd (Disk Utility sees them) and the only suggestion that seemed reasonable was, "Insert a blank CD into each drive and restart."
I did...and the result is I'm locked out of my U-10.04!  That machine is HP-m7674b IntelDuoCore -64, Nvidia GeForce 7300ls and running 64 Ubuntu 10.04.  (I'm on my other machine frantically searching)
If anyone can help, the answer could help us both.
Cheers,
Scott


You can try remounting the file system if, for some reason, it has become mounted read-only all together.  For the root FS try:

```
mount -o remount,rw /
```

---

