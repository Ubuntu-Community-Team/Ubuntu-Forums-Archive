---
title: "redirect home folder to another hard drive"
date: 2011-10-06
forum: General Help
---

### Post by nethero on 2011-10-06
My computer has two hard drives, one is 200 gB and stores my OS files for Windows 7 and Ubuntu, the other is 1 TB and I use it for storage, all my movies/music/files go here.

I'd like to set things up so my home folder resides or links to the 1TB storage hard drive, that way all my movies and files will be in my home folder.  How would I go about doing this?

---

### Post by jazzon on 2011-10-06
first step is to identify the internal identifications of the drives.

Are both drives accesible from linux?  If yes, then run 
[HTML]cat /etc/mtab[/HTML]
and post the output back to here.

You are looking for entries like 
[HTML]/dev/sda6 / ext4 rw,errors=remount-ro 0 0[/HTML]
There will be many more but there should be one for each drive.

---

### Post by nethero on 2011-10-10
Here is my output:

/dev/sda5 / ext4 rw,errors=remount-ro,commit=0 0 0
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
/dev/sdb1 /media/storage fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda2 /media/windows fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

---

### Post by dcstar on 2011-10-11
> **nethero said:**
> My computer has two hard drives, one is 200 gB and stores my OS files for Windows 7 and Ubuntu, the other is 1 TB and I use it for storage, all my movies/music/files go here.

I'd like to set things up so my home folder resides or links to the 1TB storage hard drive, that way all my movies and files will be in my home folder.  How would I go about doing this?

Linux System Folders - like /home folders - **cannot** reside on non-linux filesystems.

You may be able to link trivial sub-folders under the /home/user tree to an external non-linux filesystem but it still will have issues if Linux apps try to use it.

---

### Post by nethero on 2011-10-25
One more thing...

Is there a way I can make a link to two directories in a single shortcut and have the contents of both directories load in one window?  I have two music folders, one on one hard drive and another on the other hard drive.  It would be nice to have a desktop link that linked to both simultaneously.

---

### Post by Paddy Landau on 2011-10-26
> **nethero said:**
> Is there a way I can make a link to two directories in a single shortcut...
Unfortunately, no. When you open Nautilus, press F3; you will see the same directory in two panels. You can change one of the panels. But there is no way to do this from a shortcut.

Here is the best I can offer:

[LIST=1]
[*]Open Nautilus. Navigate to one of the folders (call it Music-1). Bookmark that folder (Ctrl-D).
[*]Now create a shortcut (launcher) for your other folder (call it Music-2). Close Nautilus.
[/LIST]
In future, you can press the launcher to load Nautilus with Music-2; press F3; select the bookmark for Music-1. Just two mouse clicks and one keypress.

---

