---
title: "unmount problem"
date: 2010-12-17
forum: General Help
---

### Post by gandaran on 2010-12-17
hi,
I use this command to mount a network drive
> sudo mount -t cifs -o guest //192.168.0.1/usb1-c/ /mnt/share
it works fine but I'm having problems to unmount the drive, what (umount) command should I use to unmount the same drive?
thanks

---

### Post by pellgarlic on 2010-12-17
just this should do it:

umount /mnt/share

---

### Post by gandaran on 2010-12-17
> **pellgarlic said:**
> just this should do it:

umount /mnt/share
simple! and I never thought of that!
thanks

---

### Post by pellgarlic on 2010-12-17
yeah, usually just "umount" folowed by either the mount point, or the /dev/xyz of the drive will do it. mount point is usually easiest to remember. =)

---

