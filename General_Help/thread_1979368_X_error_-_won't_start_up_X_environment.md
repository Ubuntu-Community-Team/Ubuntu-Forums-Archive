---
title: "X error - won't start up X environment"
date: 2012-05-13
forum: General Help
---

### Post by crw4096 on 2012-05-13
Hello,

I resized my root partition and now X won't start (followed standard procedure of booting from a Ubuntu install USB key, gparted, etc).

Everything else looks fine (all disks mounted, all files present...) but the X console doesn't start.  I've attached /var/log/Xorg.0.log for examination.  There are a couple of errors at the bottom that I don't understand:

"[drm] failed to set drm interface version"

and then a few lines later,

"Screen(s) found, but none have a usable configuration"

Anyone have an idea here?  Is there something I need to do after resizing the partition?  I can provide whatever other information you think is needed; the system is otherwise fully functional.

Thanks a lot,

Charles

---

### Post by dino99 on 2012-05-13
the resized partition has also a new uuid, and i suppose you have not updated grub then, so it still search for the old uuid.
check with : sudo blkid

---

### Post by crw4096 on 2012-05-13
Hi,

Thanks for the command pointer.  It seems the new root partition has the same exact UUID as before.  Result from blkid:

/dev/sdb1: UUID="17292248-2f71-420f-b57b-a9b48165f15e" TYPE="ext4"

Un-updated contents of fstab:

$ grep 17292248-2f71-420f-b57b-a9b48165f15e /etc/fstab
UUID=17292248-2f71-420f-b57b-a9b48165f15e /               ext4    noatime,errors=remount-ro 0       1

Also, I don't see how this matters if grub boots the machine up just fine?

Thanks,

Charles

---

### Post by crw4096 on 2012-05-13
Hi,

I found out some more info.  It seems that what's broken is just the script (or whatever) that starts up X.  If I log in to the console and type "startx", then X starts up with the Unity desktop.

By the way, I have two displays, and I can configure them "just fine" under Unity.  Unity remembers the configuration next time I start it this way.

So, something funny is going on with the X startup script - it thinks the displays are messed up.  Perhaps some file is not getting loaded in time? Any startup script experts out there?

Thanks,

Charles

---

