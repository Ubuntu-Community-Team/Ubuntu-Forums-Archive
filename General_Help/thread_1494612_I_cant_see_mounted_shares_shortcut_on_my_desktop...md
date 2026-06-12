---
title: "I cant see mounted shares shortcut on my desktop.."
date: 2010-05-27
forum: General Help
---

### Post by Elie-M on 2010-05-27
that worked fine on karmic, with samba..

after I did the 10.04 clean install and I redid the configuration, ubuntu is able to mount the windows drive on startup, but the usual shortcut that appears on the desktop for mounted drives/shares/volumes never appears.. can anyone help me solve that?

---

### Post by Morbius1 on 2010-05-27
Did you by any chance change the mountpoint from something in your /home or /media ( which will create a desktop shortcut ) to something in either /mnt or "/" ( which will not create a desktop shortcut) ?

---

### Post by Elie-M on 2010-05-27
uh oh.... if u mean when I reformatted and picked the ubuntu partition to reformat I saw a pick a mount point there, and the mount point I picked YES was /

I dunno what's the difference between different mount points :-/

---

### Post by Ozymandias_117 on 2010-05-27
> **Elie-M said:**
> uh oh.... if u mean when I reformatted and picked the ubuntu partition to reformat I saw a pick a mount point there, and the mount point I picked YES was /

I dunno what's the difference between different mount points :-/

He's referring to something else

Try opening a terminal, and then gconf-editor Browse to Apps -> Nautilus -> Desktop and make sure "volumes_visible" is checked

---

### Post by Elie-M on 2010-05-27
it is checked. I can see any partiton I mount except the windows share. that share used to automatically create a drive icon for it on the desktop

---

### Post by Morbius1 on 2010-05-27
I'm still confused by the samba reference in your original post. Is this a remote windows share on another box or an internal windows partition on the same box?

Why not post the output of the following commands so we can all see what's up:

Open **Terminal**
Type **cat /etc/fstab**
Type **mount**

---

### Post by Elie-M on 2010-05-27
it's an external windows box that has a shared folder that I mount on the network on startup. I was abt to send the fstab output on my own for those who are reading but I slept :P

aaaanywayz:

fstab output is:

[B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=082f3478-1f78-45ca-8b69-ef98e88d6d6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=928b6bab-43f3-405a-8a82-c691a1b4a3dd none            swap    sw              0       0
//192.168.1.101/Documents    /mnt/win    cifs    credentials=/etc/cred,iocharset=utf8,file_mode=0777,dir_mode=0777    0    0


[/B]and the mount is:

[B]/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/elie-m/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=elie-m)
/dev/sda3 on /media/36E43D7FE43D4303 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


[/B]

---

### Post by Morbius1 on 2010-05-27
> ** //192.168.1.101/Documents [COLOR=Blue]   /mnt/win[/COLOR]    cifs     credentials=/etc/cred,iocharset=utf8,file_mode=0777,dir_mode=0777    0     0**If you mount anything ( local or remote ) to anything other that /home or /media then it will not appear on your desktop. So you could change the above line and substitute 
```
/media/win
```for 
> /mnt/winYou will have to create /media/win first though:
```
sudo mkdir /media/win
```

---

### Post by Elie-M on 2010-05-27
so weird. cz when it was in /mnt/win b4 the format, it was working as intended with the desktop shortcut appearing and everything...

anywayz I'll try the suggested solution

---

### Post by Elie-M on 2010-05-28
I just tried the suggested solution....



and 
.
.
.
.
It WORKS!


thx man appreciated :)

---

