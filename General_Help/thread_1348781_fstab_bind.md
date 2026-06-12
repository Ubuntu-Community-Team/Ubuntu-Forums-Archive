---
title: "fstab bind"
date: 2009-12-07
forum: General Help
---

### Post by wildyoot on 2009-12-07
Hello,

I have mounted some directories using the bind option in fstab, in this format:

/dir/source /dir/dest none bind 0 0

From what I can tell looking around the web, those are the correct options. My question is: can such a configuration with bind cause problems for some applications which work on the disk? For example, in Ubuntu the disk information applet wrongly reports enormous disks as it appears to read the disk information for the bind again (treats it as another disk/partition). I don't have a "problem" with that, but I wonder if some disk scanning utilities in Ubuntu could cause problems on the disk where there are binds. For example, what would the file system check utility do?

Reason I am concerned is that I have just had a HD fail after an automatic boot-up scan a few days after setting up the bind, so I've entered the paranoid phase.

Thank you for any help.

---

### Post by lloyd_b on 2009-12-07
> **wildyoot said:**
> Hello,

I have mounted some directories using the bind option in fstab, in this format:

/dir/source /dir/dest none bind 0 0

From what I can tell looking around the web, those are the correct options. My question is: can such a configuration with bind cause problems for some applications which work on the disk? For example, in Ubuntu the disk information applet wrongly reports enormous disks as it appears to read the disk information for the bind again (treats it as another disk/partition). I don't have a "problem" with that, but I wonder if some disk scanning utilities in Ubuntu could cause problems on the disk where there are binds. For example, what would the file system check utility do?

Reason I am concerned is that I have just had a HD fail after an automatic boot-up scan a few days after setting up the bind, so I've entered the paranoid phase.

Thank you for any help.

'fsck' won't even touch those mounts (if you *try* running fsck on one of them, it'll just generate an error, because it isn't a filesystem).

Yes, the 'bind' can cause erroneous information about disk space, but other than that there should be no problems.  Such 'bind' mounts are extremely common (for instance, they're commonly used to mount directories inside of a 'chroot' for a web or ftp server).  

In short - your HD failure is in no way related to your use of the binds...

Lloyd B.

---

### Post by wildyoot on 2009-12-07
> **lloyd_b said:**
> 'fsck' won't even touch those mounts (if you *try* running fsck on one of them, it'll just generate an error, because it isn't a filesystem).

Yes, the 'bind' can cause erroneous information about disk space, but other than that there should be no problems.  Such 'bind' mounts are extremely common (for instance, they're commonly used to mount directories inside of a 'chroot' for a web or ftp server).  

In short - your HD failure is in no way related to your use of the binds...

Lloyd B.


Many thanks, that is actually some reassurance :).

---

