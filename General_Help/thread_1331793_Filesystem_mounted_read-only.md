---
title: "Filesystem mounted read-only"
date: 2009-11-19
forum: General Help
---

### Post by kc600 on 2009-11-19
After an interrupted dist-upgrade (intrepid to karmic, stupid user shuts machine down while it is installing packages), the system fails to mount the disk. Booting in recovery mode gets eth0 up and sshd running, but i can't seem to remount the disk read-write: 'umount /dev/sda1' is no problem, but after that, 'mount /dev/sda1' yields "Filesystem already mounted". This is probably taken from mtab, which can't be modified, because the disk is read-only.

In addition, the machine is an hours' drive away, so i'd like to try and fix it remotely.

Any hints, anyone?

---

### Post by Giblet5 on 2009-11-19
Ouch! I doubt that you'll fix this via remote, but you can try...

#1 Is there a recent backup of the user's data?

Focus everything on that question for now. Everything else must wait.


Edit: you could have, and probably did, drive to the site by now.

I'm outta here.

---

### Post by kc600 on 2009-11-19
Data is safe, fs is clean, etc. Edit: backup has been made, just to be sure.

Still didn't drive there... it's not that big a deal. I might have to eventually (weekend?), but try to avoid that.

Does anyone have a clue what i might actually do about the problem? ;)

---

### Post by kc600 on 2009-11-21
I've got access to the machine now, so i can modify the files on disk from a live CD. I threw away all lines from /etc/mtab, but still the same stuff.

I'm considering a complete reinstall.

This is the error message on trying a normal boot:
```
One or more of the mounts in /ets/fstab cannot be mounted:
/: waiting for /dev/disk/by-uuid/...
/tmp: waiting for (null)
swap: waiting for UUID=...
```

---

