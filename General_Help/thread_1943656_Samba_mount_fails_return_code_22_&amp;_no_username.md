---
title: "Samba mount fails return code 22 &amp; no username specified"
date: 2012-03-19
forum: General Help
---

### Post by jamesisin on 2012-03-19
I'm building another 10.04 machine.  I'm having trouble getting a samba mount to function.  This is the same mount (served from 10.04 desktop) to which all of my other machines connect.  I am using the exact same code in fstab:

```
# 20110319 SHARENAME share automount

//SERVER/SHARENAME    /media/SHARENAME        cifs    guest,iocharset=utf8 0 0
```

It does not automount and when I run sudo mount -a I get two errors repeating thrice (or more):

```
CIFS VFS: cifs_mount failed w/return code = -22
CIFS VFS: No username specified
```

(The mount command just throws the rather generic "mount: wrong fs type, bad options...".)

In case it matters, I am running the PowerPC version of 10.04.

Oh, and if I run Connect to Server I am able to mount that samba connection fine.

A little help?

---

### Post by papibe on 2012-03-19
Hi jamesisin.

Did you install 'smbfs'? 

Although, some of the samba client package is installed by default, the ability to mount a samba share requires an extra package called smbfs.

Check if it's installed:
```
apt-cache policy smbfs
```
and if it'not, simply install it:
```
sudo apt-get install smbfs
```
Hope it helps.
Regards.

---

### Post by jamesisin on 2012-03-19
Damn it.  Thanks.  I don't know how that one got skipped.

---

