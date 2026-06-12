---
title: "USB drive permissions and Unison"
date: 2006-06-02
forum: General Help
---

### Post by grsing on 2006-06-02
So I'm trying to use Unison to sync a directory on a local HD with a directory on a USB drive, but for some reason, the permissions won't allow me, and I can't seem to change the permissions on the USB drive with chmod (or change the owner to root from the user with chown).  I don't know why it won't let me change the USB drive, since, using anything but Unison, I can edit at will.  My user is given read, write, and execute permissions, group and others have none.  Sorry if this is confusing (it's confusing to me, too), if I can clarify anything, please ask.  Thanks in advance!

---

### Post by grsing on 2006-06-02
Oh, and if it helps, I tried Unison using two local HDs and it works just fine (both are owned by root, with 777 permission).

---

### Post by grsing on 2006-06-03
Very polite bump (man do these boards move fast lately, with the new release and all).

---

### Post by grsing on 2006-06-03
One last try

---

### Post by bjc on 2006-06-03
Could you post the error messages you saw and the mount command you used for the USB disk?

---

### Post by givré on 2006-06-03
Is your usb drive mount by fstab, or by gnome-volume-manager. Post here your /etc/fstab and your /etc/mtab

---

### Post by grsing on 2006-06-03
Thanks for both of your help, I found a fix using the instructions here: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221) (made a udev rule, also solves the problem with the mount point changing).

---

