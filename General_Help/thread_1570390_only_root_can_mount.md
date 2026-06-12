---
title: "only root can mount"
date: 2010-09-08
forum: General Help
---

### Post by UncleBoarder on 2010-09-08
[LEFT]I have two additional internal drives.  One is mounted  in fstab (I'll call this the first drive), one is not.  The one that is not in fstab, can be  mounted/unmounted from "Places" in the GUI.  But the one that is mounted  from fstab doesn't work from "Places".

If I umount the first drive, and then try to mount it via "Places" I get the error "only root can mount".
  
Also... I've moved my /home to the first drive.  It APPEARS that I can umount the first drive (it disappears from my desktop) yet /home is still available via Terminal.  I CAN mount it again via terminal but it does not reappear on the desktop.

UUID=e0352916-43a0-431c-bb64-08a5f3182543         /media/data     ext3         errors-remount-ro         0         0

So my questions...

1) Why won't the first drive reappear on the desktop when remounted from terminal?
2) Why can't I remount the drive via "Places".


[/LEFT]

---

### Post by gauravj on 2010-09-08
Hi
It has to do with permissions on the drive.
When you do login as normal user, you lack certain permissions.

The drive is open to root account so will be visible to root only.
Or if mounted via fstab for normal user, will be in read only mode.

Change the permissions on whole drive by
sudo chmod -R u+rwx /drive and see if it solves the problem.

---

### Post by UncleBoarder on 2010-09-08
same results.  I did...

  sudo chmod -R u+rwx /media/data
  sudo umount /media/data

Result... I can't remount via "Places" - error "only root can mount"

  sudo mount /dev/sdb1 /media/data

Result... It mounts but does not display on desktop.

---

### Post by mcduck on 2010-09-08
Just add "user" to the mount options of a drive in fstab, and the drive can then be mounted by normal users instead of root only.

Or "defaults" should work fine as well, I believe that includes the user option anyway.

like this:
```
UUID=e0352916-43a0-431c-bb64-08a5f3182543 /media/data ext3 user,errors=remount-ro 0 0
```

> 
Also... I've moved my /home to the first drive. It APPEARS that I can umount the first drive (it disappears from my desktop) yet /home is still available via Terminal.I must admit I didn't really understand this part. Of course /home is available from a  terminal, you always have a home directory and that will be /home, regardless of what drive/partition it's physically located. OS even if you move your home directory to another drive, it will still appear as /home in the directory hierarchy.

---

### Post by UncleBoarder on 2010-09-08
nope...

UUID=e0352916-43a0-431c-bd64-08a5f3182543     /media/data     ext3     defaults,user,errors=remount-ro     0     0

Can't unmount unless I'm root.

Also tried it without "defaults", just added "user"... same result.

I thought you had it... but no.  Any more ideas?

Oh and remember if I do unmount it as root, when I remount it, it does mount, but the icon doesn't show up.  What's up with that?

sudo umount /media/data
sudo mount /dev/sdb1 /media

---

### Post by UncleBoarder on 2010-09-19
The answer is the mount order...

mount a drive to /media... it shows on desktop, and can be unmounted/remounted

mount a drive to /media AND mount it to /mnt... still shows on desktop but can not be unmounted/remounted

mount a drive to /mnt AND mount it to /media... won't show on desktop

So, two mounts of the same drive must be mounted to /media first.  And if you unmount it, you'll have to unmount the second mount and remount in the same order.

This might be true for mount --bind as well.  I didn't test.

---

