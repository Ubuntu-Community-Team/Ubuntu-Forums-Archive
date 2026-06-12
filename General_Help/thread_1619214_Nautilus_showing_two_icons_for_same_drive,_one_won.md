---
title: "Nautilus showing two icons for same drive, one won't mount"
date: 2010-11-11
forum: General Help
---

### Post by Rubicon421 on 2010-11-11
For some reason I am getting two icons for the same NTFS partition under the devices section in Nautilus. One of them mounts on boot and works fine, the other one give this error when trying to access:

Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

I've noticed that the icon is slightly different for it as well. Not sure what that means. The entry for this partition in fstab reads-

UUID=66915252454E4426 /media/Basement ntfs-3g users 0 0

I used mount manager to try and fix it and didn't see any difference. Any ideas?

---

### Post by |{urse on 2010-11-11
weeeird, maybe a proprietary partition originally installed with windows? Was the original OS an OEM install or was it user-installed? Have you tried to mount it as root? you can do that as root with sudo su and the mount command. The easy way is.. 
> sudo nautilus
Then browse to your media folder and have a look-see.
What's in it?

---

### Post by mc4man on 2010-11-11
Possibly take a look at this bug, may also affect ntfs volumes that are auto mounted(fstab
The suggested workaround is shown a bit clearer in 2nd link (/dev/disk/by-uuid/[COLOR="Blue"]xxxx[/COLOR] where xxxx is the uuid of the partition

[https://bugs.launchpad.net/gvfs/+bug/442130](https://bugs.launchpad.net/gvfs/+bug/442130)
[http://ubuntuforums.org/showthread.php?p=8050320](http://ubuntuforums.org/showthread.php?p=8050320)

---

### Post by Rubicon421 on 2010-11-11
Ok, that's even more weird- the second (inaccessable) partition doesn't even show up in admin mode. 

By the way, it was a clean install of 10.04 on a new, blank HD. I just made an NTFS partition to store all my music because I was cloning it from another older backup from when I still used Windows.

---

### Post by Rubicon421 on 2010-11-11
I changed the word "users" to "default" in the fstab line for that partition and it got rid of the extra (nonworking) icon.

---

### Post by |{urse on 2010-11-13
but that just removes the mountpoint from the users group.. there's still a weird partition on that drive. You should check for rootkits on your windows installation, some of the nastier ones create odd partitions to hide themselves.

---

### Post by Rubicon421 on 2010-11-14
No, it's fine now. It was just an invalid entry in fstab. There are no extra partitions showing up in GParted, it was only in Nautilus. And there is no Windows partition. I have an NTFS partition for storing music but U10.04 is the only OS installed.

---

### Post by |{urse on 2010-11-16
ah right on

---

