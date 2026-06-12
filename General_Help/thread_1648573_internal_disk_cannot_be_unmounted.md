---
title: "internal disk cannot be unmounted"
date: 2010-12-19
forum: General Help
---

### Post by dokyounder on 2010-12-19
I have two internal disks that are accessible from my ubuntu. 
I installed ubuntu using wubi, and those two disks are the same disks I use on Windows. 
One of the disks contains windows system files. 

These disks were easily accessible from ubuntu, I could mount/unmount anytime I wanted and had no problem with editing files.

I did something I can't remember, I was just following some instruction trying to solve problem with my SD card reader. 
turned out it wasn't the right solution ([SIZE="1"]but I fixed the SD card issue using some other instruction)[/SIZE], 
now when I turn the c omputer on, the two internal disks are pre-mounted, 
and everytime I try to unmount those the following message appears.

[I]Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /media/sda1[/I]

help please

---

### Post by hoooootz82 on 2010-12-19
It sounds like you edited /etc/fstab . if you want to temporarily unmount them, you would have to do it as root, since they are internal drives. 
```
df
```
will list all your disks, you should be able to tell by their size which one is which, you will be looking for a device such as /dev/sdX, where X is a, b, c, ... to unmount, just type:
```
sudo umount /dev/sdX
```
enter your password and it should unmount it. To permanently unmount it, ***ment out the line in /etc/fstab that is mounting it, using #'s.

*edit:

should have read your post more carefully. The ***mand you can enter is
```
sudo umount /media/sda1
```
or
```
sudo umount /dev/sda1
```


also why can't you say ***?
what if i need to run a ***mand to run a braod*** wireless card to connect to a ***cast connection using my ***puter in my ***mand center?

---

### Post by dokyounder on 2010-12-19
hey thanks,
I unmounted them successfully. 
but how do I do it permanently?

This is what I have for fstab.
Those disks I'm having trouble with are sda1 and sda5.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda6	/host	fuseblk	defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096	0	0
/dev/sda1	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sda5	/media/sda5	ntfs	defaults,nls=utf8,umask=0222	0	0
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0

---

### Post by tredegar on 2010-12-20
If you do not want sda1 and sda5 to be mounted, comment them out, then they will not be mounted at the next boot.```
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda6 /host fuseblk defaults,nosuid,nodev,relatime,user_id=0,group_id= 0,allow_other,blksize=4096 0 0
[COLOR="Red"]# [/COLOR]/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=0222 0 0
[COLOR="Red"]# [/COLOR]/dev/sda5 /media/sda5 ntfs defaults,nls=utf8,umask=0222 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

---

### Post by dokyounder on 2010-12-23
Thank you. problem solved

---

