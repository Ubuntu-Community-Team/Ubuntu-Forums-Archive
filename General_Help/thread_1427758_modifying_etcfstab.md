---
title: "modifying /etc/fstab"
date: 2010-03-11
forum: General Help
---

### Post by pavel989 on 2010-03-11
ive tried so many things but i cant get it to work.

how can i modify fstab so that sdb1 on my ntfs shared drive, mounts with read/write for everyone

---

### Post by DeMus on 2010-03-11
> **pavel989 said:**
> ive tried so many things but i cant get it to work.

how can i modify fstab so that sdb1 on my ntfs shared drive, mounts with read/write for everyone

I have the following lines in my fstab for an NTFS partition:

# Entry for /dev/sdb1 NTFS disc
/dev/sdb1 /media/Video ntfs-3g defaults 0 0

Start by creating a folder in /media. In my case /media/Video.
```
sudo cd /media
mkdir Video
```

---

### Post by srs5694 on 2010-03-11
To adjust permissions, you need to use the umask, fmask, and/or dmask values as options (where "defaults" goes in DeMus's example). Type "man mount" at a shell prompt and search for those terms. As an extreme, you could use "umask=000", but this would make everything readable, writable, and executable to everybody. Chances are that "fmask=222,dmask=000" would work better. You can restrict it to certain groups for improved security, if you like.

---

### Post by hemimaniac on 2010-03-12
You could try;

sudo apt-get install pysdm

Then;

Menu>admin>Storage Manager

set to defaults, rename if you wish

apply and restart

---

