---
title: "how to run a file in iso from terminal"
date: 2012-03-10
forum: General Help
---

### Post by abdolah on 2012-03-10
hello
i have an iso file ( App.iso) and i can mount it ,but i don't know the address of it to change directory there, how i can change directory to it to run a file in it?
when i copy it and paste it into the command line shows me:
archive://file%253A%252F%252F%252Fmedia%252FZolfaghar%252FApp%252FLinux%252FApp.iso/app.exe
but with this address i cann't do anything.

---

### Post by MSPdwalt on 2012-03-10
What was the command you used to mount it?  Usually when you mount something you tell it where to mount to.

If you used something other than the baked in mount command try looking under /media or do an ls on your home directory and see if there's a directory named after your iso.

furiusisomount is a really sweet package that makes iso mounting a breeze and will show you where it mounts them to.

---

### Post by abdolah on 2012-03-11
I only click on it and it become mounted but i don't know where it has been mounted , and also it hasn't been mounted on /media or my home directory.

---

### Post by wallaroo on 2012-03-11
Similar to auto-mounted Samba shares, you should find that the ISO file has been mounted in the .gvfs folder in your home directory.

---

### Post by sudodus on 2012-03-11
Try ```
cat /etc/mtab
```
because if your iso file is mounted, there should be information about it in mtab. If you are not sure what you see, please post the output of that command!

---

### Post by abdolah on 2012-03-11
it has been mounted in 
/home/abdolah/.gvfs/App.iso 
or
archive://file%253A%252F%252F%252Fmedia%252FZolfaghar%252FApp%252FLinux%252FApp.iso/
but i cannot change the permission of files in it even with sudo and super user!!
when i right click on it and see the permision it shows: the permision could not be determined.

abdolah@abdolah-laptop:~$ cat /etc/mtab
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/abdolah/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=abdolah 0 0
/dev/sda4 /media/Zolfaghar fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda2 /media/F680883B80880479 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
abdolah@abdolah-laptop:~$

---

### Post by sudodus on 2012-03-11
I mounted an iso file in my own computer and it has only read access for the user. So you should be able to read the files inside it ,'extract' it (making a copy of its files. And then you can change the permissions of those copies (if you are working in a linux file system). This can be done with the archiver or via terminal commands.

---

