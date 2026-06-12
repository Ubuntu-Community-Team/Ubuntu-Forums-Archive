---
title: "I thought root could do anything :)"
date: 2010-01-01
forum: General Help
---

### Post by OldGrantonian on 2010-01-01
I have dual-boot XP/Karmic

I have an external HDD for backup. One partition is NTFS for the XP stuff. The second partition is ext4.

I was practicing with the SystemRestoreCD, which provides a Linux root console. 

I can create and delete directories on the ext4 partition, but not on the NTFS partition. The error message says "read-only file system".

The permissions on the NTFS partion are:

rwx --- ---  myName     myName

I tried to use chmod and chown to change permissions and owner.

I assumed that as root, I could do anything.

How can I access the NTFS partition, and do anything that I need to do?

BTW:  All my current XP stuff on the HDD was backed up from within XP, using standard software (Cobian Backup), and normal user privileges. But I want to practice for when my XP OS is damaged.
.

---

### Post by 4pack on 2010-01-01
Offhand, it sounds like the partition is mounted Read Only, not Read Write.

It's like if you take the little tab on an SD card and slide it to "Lock", then even root wouldn't be able to write to it.

You likely need to unmount it and then remount it with the RW option.

---

### Post by Leppie on 2010-01-01
the ntfs partition needs to be mounted as read/write.
the fact that this system mounts it as read-only, may indicate that it's better not to mount ntfs partitions in read/write mode (this may be due to many factors like no stable ntfs module or tools to modify a partition at low level which could prevent windows from booting later on).

but if you really want to try it, you should first unmount the partition:
```
umount /your/device
```
or
```
umount /mount/point
```

after which you can mount it in read/write mode:
```
mount -t ntfs -rw /your/device /mount/point
```

**_NOTE:_** *if the ntfs module is unstable, mounting the ntfs partition in read/write mode may cause serious damage to the filesystem.*

---

### Post by The Cog on 2010-01-01
Another possible reason for a readonly NTFS mount is that it wasn't shut down cleanly. If this is the case, you'll have to mount it in windows and then unmount it again - I don't think Linux can do an NTFS chkdsk.

---

### Post by Leppie on 2010-01-01
> **The Cog said:**
> Another possible reason for a readonly NTFS mount is that it wasn't shut down cleanly. If this is the case, you'll have to mount it in windows and then unmount it again - I don't think Linux can do an NTFS chkdsk.

yeah, you're right, linux cannot do the ntfs chkdsk. this is also a reason why not to do a wubi install...

---

### Post by ibuclaw on 2010-01-01
1) Unix File Permissions don't apply to NTFS filesystems. You can only mount it using a premeditated permission that gets enforced for all files/directories.

2) If the filesystem has been mounted as read-only, was probably unmounted uncleanly. Mounting/Unmounting in Windows usually resolves this.
If not an option - I do believe there is an ntfs-fix command you can run on to fix all/any journal errors.

Regards
Iain

---

### Post by sdowney717 on 2010-01-01
[http://kunalghosh.wordpress.com/2009/04/05/ntfsfix-a-life-saving-command/](http://kunalghosh.wordpress.com/2009/04/05/ntfsfix-a-life-saving-command/)
ntfsfix never have run this yet.

---

### Post by OldGrantonian on 2010-01-01
Thanks for all the responses :)

But no luck.

I tried the suggestions in (hopefully) the most efficient order.

Reboot to Windows, eject the HDD, switch off HDD.

Reboot to SystemRecoveryCD console. 

Switch on HDD. Mount HDD.

```

ntfsfix ........

```

Got the message:

"... processed successfully"

Type "mount". Message says partition is "ntfs (rw)"

But I could not create a directory.

I then tried to force a read/write mount with:
```

mount -t ntfs -rw /your/device /mount/point

```

Again, I could not create a directory.

BTW:  I just found out that I can write to the Windows HDD partition from Ubuntu !!

This means that I can write to the Windows HDD partition both from Windows and from Ubuntu, but not from the SystemRescueCD. Is that a clue?

I intended to use fsarchiver to do the XP OS partition backup. (It works for my Ubuntu OS partition.)

Is it OK to run fsarchiver from Ubuntu, so that I'm not using the Windows XP partition while it's being backed up (which is the point of using a live CD)?
.

---

### Post by OldGrantonian on 2010-01-02
Thanks for all the responses :)

The trick is to use ntfs-3g, rather than ntfs

Here is my successful command:

```

mount  -t  ntfs-3g  /dev/sdb1  /mnt/freecom  -o  defaults,umask=0

```Note that the umask stuff might be overkill, because without umask, I get the default R/W permissions.
.

---

