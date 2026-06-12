---
title: "Write Permissions...?"
date: 2006-04-06
forum: General Help
---

### Post by oolunchbox on 2006-04-06
Ok I must be some sort of moron.  I've tried everything I can find to mount my 2 SATA storage drives and no matter what I do I can't give myself write permissions.  I want to use them as storage like I did when I used Windows.  I had my 74GB raptor as my OS drive and my 2 200GB drives as storage so I could wipe the OS as needed and not lose any data.  I've been able to mount them and write them with sudo commands in the console but that's really a pain in the @$$ when I'm trying to rip CDs to them and the such.  Please someone show me the light.  They're formatted ext3 and I've gotten them mounted to various mount points. I just cannot write to them. ](*,)

---

### Post by taurus on 2006-04-06
In your /etc/fstab, add "umask=0000" after the defaults so it would look something like
```

/dev/hdb1  /media/backup  ext3  defaults,umask=0000  1  1

```

---

### Post by oolunchbox on 2006-04-07
ok this is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/sda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb1 	/mnt/sata1 	ext2 	defaults,umask=0000  1  1
/dev/sdc1 	/mnt/sata2 	ext2	defaults,umask=0000  1  1

```
and i still cannot write to the drives.  I'd ideally like to have them show up as individual drives as they did in windows.  They have been formatted and are wiped clean, so theres not NTFS problems.  I just can't figure this out.

---

### Post by amohanty on 2006-04-07
> /dev/sdb1 	/mnt/sata1 	ext2 	defaults,umask=0000  1  1
/dev/sdc1 	/mnt/sata2 	ext2	defaults,umask=0000  1  1

the **defaults** up there means that root owns it try replacing:
> defaults,umask=0000
with something like this:
> rw,auto,user,umask=0200

HTH
AM

---

### Post by oolunchbox on 2006-04-07
when i did some diggin i found that i was user 1000, should i put umask=1000?

---

### Post by Sutekh on 2006-04-07
Umask don't work for ext3 but chown and chmod do.  

Just make sure that you apply them when the **partitions are mounted**.  That way it will stay permanent.

```
sudo chown -R user.user /mnt/sata1
sudo chown -R user.user /mnt/sata2
```to change the ownership to user

```
sudo chmod -R 777 /mnt/sata1
sudo chmod -R 777 /mnt/sata2
```to change the permissions to read/write/execute.

---

### Post by amohanty on 2006-04-07
> Umask don't work for ext3

hmm didnt know that! well you learn something new everyday :)
Thanks.
AM

---

### Post by Sutekh on 2006-04-07
I only really experimented with this just the other day.

Chmod and chown will work for ext3 partitions, but like I said they must be mounted first.  If you chown and chmod the folder with partitions unmounted, then when they *are* mounted, the ownership/permissions change again.

You could probably just go straight out and chown/chmod the actual devices - /dev/sdb1 and /dev/sdc1. 

I haven't tried that yet, only to the mount points.

---

### Post by oolunchbox on 2006-04-07
WAHOO!!! THANK YOU THANK YOU THANK YOU! FINALLY! Now another noob question, how can I mount them to show up in my storage media folder? I'm using Kubuntu and I'd like quick access if i need to get to files. It seems if i create mount points in /media/ they dont show up from the menu when i pick storage media.  is that reserved for removable storage?

---

### Post by Sutekh on 2006-04-07
Strange, if I mount folder to /media in GNOME then they do appear in removable media, but then I don't have much experience using KDE.  

I noticed that your fstab has them in /mnt, have you changed them to /media?

---

### Post by amohanty on 2006-04-07
[QUOTE=Sutekh]Strange, if I mount folder to /media in GNOME then they do appear in removable media, but then I don't have much experience using KDE.  

I noticed that your fstab has them in /mnt, have you changed them to /media?[/QUOTE]


_anything_ thats in /etc/fstab can be mounted by using something like:

**mount mount_point_in_fstab**

AM

---

