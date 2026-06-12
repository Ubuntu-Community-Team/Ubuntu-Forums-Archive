---
title: "Where's my Creative Zen being  Mounted?"
date: 2011-08-07
forum: General Help
---

### Post by Matt Pellegrini on 2011-08-07
When i connect my creative Zen it's mounted as i can see it on the desktop, however when in terminal i do 

cd /media
ls

only the mounted windows drive is listed, where is the creative zen mounted? and why? Thanks,

Matt

---

### Post by SavageWolf on 2011-08-07
What is the output for: ```
mount
```

---

### Post by Matt Pellegrini on 2011-08-07
That would be:

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda3 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)

Thanks

---

### Post by NightwishFan on 2011-08-07
Perhaps it is mounted on a Gnome virtual filesystem. Check under .gvfs under your home folder.

---

### Post by Matt Pellegrini on 2011-08-07
nope nothing in .gvfs
Thanks though

---

### Post by WorMzy on 2011-08-07
Doesn't look like it is mounted. What does double-clicking the icon do/where does it take you?

---

### Post by Matt Pellegrini on 2011-08-07
It opens nautilus i can browse the files and play .mp3 files from the device. But ./media doesn't list it.

This is frustrating as i'm trying to get it to sync with rhythmbox or something which doesn't work and so i thought i'd settle with just cp files from the terminal but i can't seem to find the path to the zen from the terminal.

Thanks all for the continued help

---

### Post by coldraven on 2011-08-07
If you can browse in Nautilus try pressing Ctrl+L. This toggles the path/breadcrumb display.

---

### Post by Matt Pellegrini on 2011-08-08
Thanks for that, the location says:

 gphoto2://[usb:002,003]/

i still have no idea how to access this in terminal, i have tried a few obvious things /gphoto2 doesn't exist neither does ~/gphoto2

Anyone know what this address means or how i can change it to mount at /media like it should.

Thanks
Matt

---

### Post by WorMzy on 2011-08-08
That's a gvfs URI, so as far as I know, it *should* also be accessible via ~/.gvfs/

Try checking there while you have the folder open.

---

### Post by Matt Pellegrini on 2011-08-08
ah okay it is there thanks, but why is it there? why is it called "gphoto2 mount on usb%3A002,004" ? and how to i get it to mount under /media?

thanks

Matt

---

### Post by WorMzy on 2011-08-08
> ah okay it is there thanks, but why is it there? why is it called "gphoto2 mount on usb%3A002,004" ?

Presumably because it's being mounted using the gphoto2 backend for gvfs.

> how to i get it to mount under /media?

Add it to fstab. I'm not sure how you'd write an entry for it though. I don't know what filesystem it uses, or how you would identify it.

You could create up a symoblic link to the folder in /media though, if you want.

```
sudo ln -s /home/matt/.gvfs/**foldername** /media/zen
```

But if the folder name changes in ~/.gvfs, then the symbolic link will break.

---

### Post by Matt Pellegrini on 2011-08-09
Thanks, that's not entirely solved but it'll do for now, if anyone knows how to change where my device mounts please reply, thanks to everyone fore their help.

---

