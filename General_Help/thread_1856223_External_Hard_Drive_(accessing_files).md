---
title: "External Hard Drive (accessing files)"
date: 2011-10-07
forum: General Help
---

### Post by T08E on 2011-10-07
Hey, I am having fairly massive problems with Windows at the mo, thought it was my computer for a bit, but everything seems to be running smoothly in Ubuntu which I've not used very much (I imagine I'll be using it a lot more if windows keeps playing up).

My external hard drive shows on the desktop, and looking at the properties it says I've used 50GB, but does not show my files (says contents: nothing).

Do you know why this might be, how might I go about accessing the files?

Regards, Tobe

---

### Post by jazzon on 2011-10-07
A question firts.  (actualy a few)

1)  Is the HD USB?
2)  Is there more than one partition on it?
3)  What is/are the filesystem types (as in NTFS, EXT2, etc.)   (probably NTFS if you formated the drive under win XP or newer, but that info can help)

Something else that will  help.  Go to your menus (top left of screen) and choose Applications -> Accessories -> Terminal, and type in "mount" (no quotes).  Post the output here.

---

### Post by T08E on 2011-10-08
Thank you for the response jazzon,

1) Yes the hard drive is USB
2) The hard drive is not partitioned
3) I'm not sure on the format to be honest,I just used it straight of the box in windows 7... Its Western Digital if that helps?

The output from terminal is:


/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/toby/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=toby)


Also, not sure this helps but if I try to access the hard drive it says:

Unable to mount My Passport

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by jazzon on 2011-10-08
To8e,

Sorry but i was helping several people the other day and lost track of this thread..

Are you booting the computer with this attached? Or just plugging it in afterwords?

Also it looks like you are running a live cd? (or a possibly a WUBI install (I have never actually seen one of those so thats a guess) )

---

