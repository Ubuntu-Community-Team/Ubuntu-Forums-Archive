---
title: "Drive and Folder Permissions"
date: 2011-04-22
forum: General Help
---

### Post by ericzmeh on 2011-04-22
Seems I have done something wrong trying to share my drives on the LAN.  Yesterday I downloaded Samba, attempted to share drives on the LAN, and now I cannot access my drives through the file explorer nor terminal, nor can I mount any locations.

I seem to remember following a tutorial for sharing drives and chmoded my /media dir to 666.  Now I can not access my secondary drives :-/  

Running  sudo fdisk -l in terminal does show all drive locations succesfully.  Upon boot, the drives are visible in explorer, but clicking on them causes them to disappear, and they do not mount successfully.  
> sudo mount -t ntfs-3g /dev/sdb1 /media/XviD
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.


I'm lost at this point, and do believe I screwed up my permissions pretty good.  Help me out Ubuntu'ers :-]  I'm running Natty 11 with all updates.

---

### Post by JKyleOKC on 2011-04-22
Change /media back to 644 and see if that helps. Also, log out and back in since some settings are stored only at log-in time.

Several directories get special treatment, and for security reasons must be read-only for both the "group" and "others" categories, with only the owner allowed to write. In addition, /media must be owned by root so if you changed its owner, put it back to root as both the owner and the group.

The read and write permissions for devices that mount under /media are set by the appropriate line in /etc/fstab or in some cases by the udev rules that are invoked when the device is detected, not by the permissions of the directory itself.

---

### Post by ericzmeh on 2011-04-22
Thanks for the response JKyle

I did:  sudo chmod 644 /media, and then logged out and back in.  The drives still fail to show.  I right clicked on media folder in explorer, and ticked properties and permissions tab.  The owner reads as root, however, the group also reads root.  Apparently, I'm not the owner and cannot change permissions.

> 
ls /media
ls: cannot access /media/BigGreen: Permission denied
ls: cannot access /media/SCRATCH: Permission denied
ls: cannot access /media/XviD: Permission denied
ls: cannot access /media/XviD_: Permission denied
ls: cannot access /media/System Reserved: Permission denied
ls: cannot access /media/CC5CB1E15CB1C68C: Permission denied
ls: cannot access /media/TERA: Permission denied
BigGreen  CC5CB1E15CB1C68C  SCRATCH  System Reserved  TERA  XviD  XviD_

But,
> 
sudo ls /media
BigGreen  CC5CB1E15CB1C68C  SCRATCH  System Reserved  TERA  XviD  XviD_

And remounting produces the same result
> 
sudo mount -t ntfs-3g /dev/sdb1 /media/XviD
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.


I accessed /etc/fstab with nano and do not see any setttings for the drives.

---

### Post by JKyleOKC on 2011-04-22
Try ```
sudo umount /media/XviD
```and then try your mount command again. That should free the device up. Did you log off and then log back in after changing the /media permissions? That should have automatically unmounted all of the devices that were mounted there, and also automatically deleted their folders leaving /media empty...

EDIT: Sorry, I was in too much of a hurry to respond and failed to notice that you had done the out-in dance. If using the "umount" command works, you might try using it on each of the devices that you listed in case they're being persistent, although it's my understanding that a mount done by a user will automatically unmount when that user logs off.

And if "umount" doesn't clear things up, you might need to restart the system. I know that the reboot actions do force all devices to be unmounted.

Final thought: in a terminal, do "mount" with no parameters. It will give you a list of all mounted devices. Post that output here and it will be easier to see what is happening!

---

### Post by ericzmeh on 2011-04-22
```

sudo umount /media/XviD
umount: /media/XviD: not mounted

```

I did log out and back in after admninistering chmod command :-]

```

sudo umount /media/XviD
umount: /media/XviD: not mounted
apollo@athos:~$ sudo umount /media/XviD_
apollo@athos:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/XviD
apollo@athos:~$ cd /media/XviD
bash: cd: /media/XviD: Permission denied

```

Seems the drive was mounted to XviD_, but I can still not access any of the drives after mounting again.

and as you requested:
```


mount
/dev/sde2 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sde1 on /media/SCRATCH type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/TERA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1 on /media/BigGreen type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/CC5CB1E15CB1C68C type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/apollo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=apollo)
/dev/sdb1 on /media/XviD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

---

### Post by Morbius1 on 2011-04-22
You need the execute bit set on directories or else you won't be able to open them:

```
sudo chmod 0755 /media
```

Odd number octal indicates the execute bit is set.

---

### Post by ericzmeh on 2011-04-22
**Bows to Morbius**

All drives are now accessible :-]  Thanks so much all, don't know what I would do without my scratch drive.

---

