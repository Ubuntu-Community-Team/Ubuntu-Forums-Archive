---
title: "Samba share mounting - from 'mount' to fstab"
date: 2010-03-21
forum: General Help
---

### Post by Lockheed on 2010-03-21
I have a command line that mounts the disk of my mobile
```
sudo mount -t cifs -o user=juha //192.168.7.70/Disk_E /media/e70

```
It works, but there is a problem with it. Every folder and file has root:root ownership, so I am unable to change anything. Even when I change permissions manually, it does not work.

Now, I want to move this to fstab but have no idea how an fstab line should look like. Obviously, I want to also have rw access to the disk.

---

### Post by 666f6f on 2010-03-21
That should do it

//192.168.7.70/Disk_E /media/e70 smbfs user=WINDOWS_USER,uid=LINUX_USER,gid=LINUX_GROUP 0 0

You may omit the last two 0s, the default value is 0 anyway.

---

### Post by Lockheed on 2010-03-22
> **666f6f said:**
> That should do it

//192.168.7.70/Disk_E /media/e70 smbfs user=WINDOWS_USER,uid=LINUX_USER,gid=LINUX_GROUP 0 0

You may omit the last two 0s, the default value is 0 anyway.

What do you mean by **user=WINDOWS_USER**? The disk is actually an SD card inside my wifi-enabled Nokia mobile. 

And why **smbfs**, if I am using **cifs** to mount it manually?

---

### Post by 666f6f on 2010-03-22
In your case, I think *user=WINDOWS_USER* should read *user=juha*. It's the windows user that has access to the samba/windows share.

Also, I belive *cifs* will work just fine, since I think it's a shortcut to *smbfs* (or the opossite if you like). In any case, you can try both and see which one works for you.

---

### Post by Lockheed on 2010-03-22
Hmm, the line you proposed does not work:
```
mount: wrong fs type, bad option, bad superblock on //192.168.7.70/Disk_E,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by 666f6f on 2010-03-22
Have you tried with *cifs*?

UPDATE: Actually I according to [this post]("http://ubuntuforums.org/showthread.php?t=483184"), cifs is not the same as smbfs. Hmmm.. seems someone hasn't done his homework :>

---

### Post by Lockheed on 2010-03-22
> **666f6f said:**
> Have you tried with *cifs*?
Ha! It worked. Thanks mate!

---

### Post by 666f6f on 2010-03-22
Great, glad it worked \\:D/

---

