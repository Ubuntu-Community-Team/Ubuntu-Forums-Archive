---
title: "Auto-Mount USB drive"
date: 2011-07-23
forum: General Help
---

### Post by STPitcher on 2011-07-23
I'm running 64 bit Ubuntu, 11.04.

When I first installed, I could plug in my USB thumb drive and it was automatically mounted for me.  Lately, this no longer happens... I use the Disk Utility to mount it manually.

Any idea what I did wrong to lose this automatic mounting??

- stp

---

### Post by zero244 on 2011-07-23
You might try to make sure you safely remove the drive before you unplug it.
Right click on the drive icon in nautilus or the desktop and select safely remove drive.
Linux may not auto mount a fat or ntfs drive if it is not shut down properly.

---

### Post by vanadium on 2011-07-23
Indeed, have the file system of your USB thumb drive checked.

---

### Post by STPitcher on 2011-07-23
Nope... I'm pretty good about properly dismounting it... and it comes up no problems when manually mounted from the Disk Utility.

I'm wondering what component is involved in mounting these things as soon as they're plugged in.

Also I'm dual booted, and it used to, but no longer automatically mounts my Windows partition during either login or startup.  Undoubtedly the same problem.

Thanks for the replies, though.

- stp

---

### Post by vanadium on 2011-07-23
Not sure, but in that case check gconf-editor. /apps/nautilus/preferences/media_automount must be checked for media to mount automatically. I would not know how one could accidentally turn that off, though.

---

### Post by STPitcher on 2011-07-23
Thanks... gconf-editor is new to me... Undoubtedly a lot of good stuff in there...and plenty to shoot my foot with :-)

But its in fact, checked.

Perhaps the next step would be... Who (what component) is responsible for reading and acting on that AutoMount flag?

- stp

---

### Post by bapoumba on 2011-07-23
Please paste the output to ```
cat /etc/mtab
``` with your USB drive plugged in.
Here is for example the last line I have with a USB stick :
```
/dev/sdb2 /media/USB_Storage_HFS hfsplus rw,nosuid,nodev,uhelper=udisks 0 0
```

Anything that is mounted in /media should show up automatically on your desktop and file browser. May be you got it mounted to some other file ?

---

### Post by STPitcher on 2011-07-23
This device is not mounted in /media!!  I want to get it mounted!!

Here's mtab.

/dev/sda6 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda2 /media/90FA5288FA526B0C fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

---

### Post by bapoumba on 2011-07-23
What is the /dev/sda2 mounted in /media ?
When you open Disk Utiliy, where does the USB stick appear to be mounted ?

Please also post:
```
cat /etc/fstab
```

---

### Post by Mikhail Titov on 2011-07-29
> **STPitcher said:**
> Also I'm dual booted, and it used to, but no longer automatically mounts my Windows partition during either login or startup.  Undoubtedly the same problem.If you did repartitioning/restoring and ended up with an empty partition, this might be relevant [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038)

---

