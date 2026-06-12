---
title: "mount problems"
date: 2011-04-04
forum: General Help
---

### Post by freshtoast on 2011-04-04
Hello all

I'm really scratching my head on this one - I'm trying to mount a USB hardrive from the terminal.

Using the following I can mount the hdd:
```
sudo mount -o rw,users /dev/sdb1 /mnt/usbhd
```

However if I try and change to /mnt/usbhd :
```
-bash: cd: /mnt/usbhd: Permission denied
```
(if I change to root I can view the contents)

If I add umask=000 I can view the contents, but I can't do anything to them:
```
sudo mount -o rw,users,umask=000 /dev/sdb1 /mnt/usbhd
```
```
mkdir: cannot create directory `misc': Read-only file system
```

I have tried changed the privileges of /mnt/usbhd, and I have tried adding an entry into /etc/fstab (and restarted), and I have tried using "user" rather than "users" but I get exactly the same results.

I don't have autofs or usbmount installed, which I read somewhere causes issues.

Where am I going wrong?!

-- Added --
when mount is ran:
```
/dev/sdb1 on /mnt/usbhd type ntfs (rw,nosuid,nodev)
```

--- Added again ---
I've run these commands on another machine and it works perfectly, so it isn't the drive...?!

---

### Post by freshtoast on 2011-04-04
I managed to find a solution to this:
The USB HDD was formatted in NTFS, so after installing ntfs-3g it worked

It took a long time to figure that out, so hopefully that may help somebody else who is struggling with a similar problem

---

