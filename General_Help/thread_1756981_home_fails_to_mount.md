---
title: "/home fails to mount"
date: 2011-05-12
forum: General Help
---

### Post by Vi3GameHkr on 2011-05-12
Good Evening,

So a few hours ago I opened up GPartEd from a live CD, and one of my operations was moving the /home partition up a little.  In the process, it was changed from /dev/sda8 to /dev/sda7.  Well upon the next boot, /home failed to mount.  I edited /etc/fstab (and apparantly DropBox had just commented out the line that mounts /home so I have NO IDEA how /home was being mounted before) and still no dice.  So every time I boot, I have to go to manual recovery and type mount /home before I can boot.

Is there some way I can mount /home without making a "git 'er done" script?

On a side note, Google Chrome has refused to open since the partition editing.

Oh, and, in case it is helpful, here's the contents of /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=33bb50c2-a5f7-463b-8ac1-97bf7207d877    /    ext4    errors=remount-ro    0    1
# Commented out by Dropbox
/dev/sda7    /home    ext4    defaults,commit=0,commit=0,user_xattr    0    0
/dev/sda2    /files    ntfs-3g    defaults,locale-en_us.UTF-8    0    0
#Entry for /dev/sda2 :
#UUID=AC702392702361F6    /media/Files    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda6 :
UUID=4fbebeb6-b9ca-4e12-926d-3ffdf6853df4    none    swap    sw    0    0


/dev/sda8 /home ext4 defaults,commit=0,commit=0,user_xattr 0 0

---

### Post by Vi3GameHkr on 2011-05-12
Sorry guys,

I don't know why I didn't catch the bottom line (which DropBox probably added).  Thanks anyways I guess.

Sincerely,
Vi3 the stupid

P.S. Chrome still doesn't start

And actually, (in case someone else runs into the same trouble) I ran google-chrome from terminal and got
> $ google-chrome
[3378:3388:354453528:ERROR:shared_memory_posix.cc(154)] Creating shared memory in /dev/shm/.com.google.chrome.BMNt3S failed: Permission denied
[3378:3388:354453626:ERROR:shared_memory_posix.cc(157)] Unable to access(W_OK|X_OK) /dev/shm: Permission denied
[3378:3388:354453636:FATAL:shared_memory_posix.cc(159)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
Aborted
and upon running sudo chmod 1777 /dev/shm, it worked.  No idea why that wasn't already set.  Have a good night.

---

### Post by sparkler on 2011-05-12
do sudo blkid then put the uuid for /home into fstab instead of /dev/*** etc otherwise it will fail to mount everytime /dev/*** changes

---

