---
title: "couldn't mount ntfs partitios after installing pysdm"
date: 2011-08-07
forum: General Help
---

### Post by Naruto Man on 2011-08-07
i couldn't mount any partition of ntfs partitions after installing pysdm

---

### Post by Morbius1 on 2011-08-07
It's not your fault it's Pysdm's.

Please post the output of each of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by Naruto Man on 2011-08-07
> **Morbius1 said:**
> It's not your fault it's Pysdm's.

Please post the output of each of the following commands:
```
sudo blkid -c /dev/null

[COLOR=Red]/dev/sda1: UUID="BCB47389B47344C4" TYPE="ntfs" 
/dev/sda5: UUID="E24C681D4C67EAAD" TYPE="ntfs" 
/dev/sda6: UUID="5ba4121e-a821-422f-b372-6066693fe6a8" TYPE="ext4" 
/dev/sda7: UUID="278e0920-89ea-419c-9d27-fb82194b52a1" TYPE="swap" 
/dev/sda8: UUID="0604A69104A682F3" TYPE="ntfs" 
/dev/sda9: UUID="BEB0AB2DB0AAEADB" TYPE="ntfs" 
/dev/sda10: UUID="3E1CB0A61CB05B1B" TYPE="ntfs" 
/dev/sda11: UUID="F870B5B970B57F46" TYPE="ntfs"[/COLOR]

cat /etc/fstab

[COLOR=Red]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                              0  0  
# / was on /dev/sda11 during installation
UUID=5ba4121e-a821-422f-b372-6066693fe6a8  /               ext4  errors=remount-ro                                0  1  
# swap was on /dev/sda10 during installation
UUID=278e0920-89ea-419c-9d27-fb82194b52a1  none            swap  sw                                               0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8                         0  0  
/dev/sda8                                  /media/sda8     ntfs  nls=iso8859-1,users,noauto,umask=000,user,owner  0  0  
/dev/sda5                                  /media/sda5     ntfs  nls=iso8859-1,users,noauto,umask=000,user,owner  0  0  
/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,ro,users,noauto,umask=000          0  0  
/dev/sda9                                  /media/sda9     ntfs  nls=iso8859-1,users,noauto,umask=000,user        0  0[/COLOR]  

mount

[COLOR=Red]/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
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
gvfs-fuse-daemon on /home/naruto/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=naruto)[/COLOR]


```

my answer in red
thanks

---

### Post by Morbius1 on 2011-08-07
* All of your ntfs statements in fstab have the "noauto" option which tells the system not to automatically mount them on boot.

Is that what you want it do do or was your intent to have it automount on boot?


* You've got some contradictory options set on this one:
> [COLOR=Red][COLOR=Black]/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,ro,users,noauto,umask=000          0  0[/COLOR]  [/COLOR]noauto - it won't mount automatically
ro - This tells the system to mount the partition "read only". 
umask=000 - tells the system to allow read/write to everyone.

What was your intent on this one. To mount it read only or to have it read/write by everyone?

---

### Post by Morbius1 on 2011-08-07
I'm making this more complicated than it needs to be. This is simpler I think:

[1] If you don't want it to automount then go back to mounting it through Nautilus by placing a "#" sign in front of each ntfs line like this:
> #/dev/sda8                                  /media/sda8     ntfs  nls=iso8859-1,users,noauto,umask=000,user,owner  0  0  
#/dev/sda5                                  /media/sda5     ntfs  nls=iso8859-1,users,noauto,umask=000,user,owner  0  0  
#/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,ro,users,noauto,umask=000          0  0  
#/dev/sda9                                  /media/sda9     ntfs  nls=iso8859-1,users,noauto,umask=000,user        0  0[2] If you do want it to automount then change the lines to this:
> /dev/sda8                                  /media/sda8     ntfs  defaults,nls=iso8859-1,umask=000  0  0  
/dev/sda5                                  /media/sda5     ntfs defaults,nls=iso8859-1,umask=000  0  0  
/dev/sda1                                  /media/sda1     ntfs  defaults,nls=iso8859-1,ro,umask=222          0  0  
/dev/sda9                                  /media/sda9     ntfs  defaults,nls=iso8859-1,umask=000        0  0After you do [1] or [2] run the following command which will test for errors and run the new lines in fstab:
```
sudo mount -a
```

---

### Post by Naruto Man on 2011-08-08
> **Morbius1 said:**
> * All of your ntfs statements in fstab have the "noauto" option which tells the system not to automatically mount them on boot.

Is that what you want it do do or was your intent to have it automount on boot?


* You've got some contradictory options set on this one:
noauto - it won't mount automatically
ro - This tells the system to mount the partition "read only". 
umask=000 - tells the system to allow read/write to everyone.

What was your intent on this one. To mount it read only or to have it read/write by everyone?

[COLOR=Red]thanks for answering me[/COLOR].
[COLOR=Red]the problem is that i can't mount any of my ntfs partitions manually after installing pysdm it requires to be root[/COLOR]
 
> **Morbius1 said:**
> I'm making this more complicated than it needs to be. This is simpler I think:

[1] If you don't want it to automount then go back to mounting it through Nautilus by placing a "#" sign in front of each ntfs line like this:
[2] If you do want it to automount then change the lines to this:
After you do [1] or [2] run the following command which will test for errors and run the new lines in fstab:
```
sudo mount -a
```

[COLOR=Red]thanks after putting # before each line of ntfs partitions the partition is mounted manually without needing root permission[/COLOR]

---

