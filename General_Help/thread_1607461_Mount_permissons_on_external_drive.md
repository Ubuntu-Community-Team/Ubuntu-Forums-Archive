---
title: "Mount permissons on external drive"
date: 2010-10-27
forum: General Help
---

### Post by jonasg on 2010-10-27
I've got an external drive that is formatted using the FAT32 filesystem.

My fstab file contains the following line:


/dev/sdb2       /media/lada     vfat    noatime         0       1


This device is now mounted as such:


drwxr-xr-x 25 root root 32768 1970-01-01 01:00 lada


I'd rather see the device or directory to belong to the media group.

This doesn't work while mounted:



jonas@Hades:/media$ sudo chown :media lada
[sudo] password for jonas:
chown: changing group of `lada': Operation not permitted


So I tried to unmount the drive, then change the permissions and remount. This also doesn't help because the permissions are restorted after every mount.

Any guidance is welcome.

---

### Post by oldfred on 2010-10-27
FAT & NTFS do not support ownership and permissions:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
**Ownership and permissions of vfat / ntfs are set at the time of mounting**. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

This was what I use when I use FAT as my shared. I now use NTFS as FAT is not so good anymore. 4GB limit on file size & no journal.
# Entry for /dev/sda4 :
UUID=46CD-C9B2                             /media/share   vfat         user,auto,fmask=0111,dmask=0000      0  0

---

### Post by WorMzy on 2010-10-27
Change the 1 on the end of the fstab line to a 0 or a 2, only the root partition (the one used as /) should have a 1. I'd recommend a 0 for a FAT## partition, that means that fsck won't check it for errors. 2 would check the partition for errors, but I don't know if fsck can check FAT or not.

I wrote this tutorial for NTFS partitions, but it should work the same way for FAT partitions: [[COLOR="Blue"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by Morbius1 on 2010-10-27
> /dev/sdb2       /media/lada     vfat    noatime         0       1

Try this:
```
/dev/sdb2       /media/lada     vfat    noatime,gid=media         0       2
```
The gid=media will change the group to "media" if that's your group name.

Then unmount the current partition:
```
sudo umount /media/lada
```
The following command will check for errors and mount it with the new ownership:
```
sudo mount -a
```

---

### Post by Morbius1 on 2010-10-27
Came back to check up on things and noticed WorMzy's HowTo link. It appears we are saying the same thing. Sorry for the echo :wink:

---

### Post by pbhill on 2010-11-07
> **WorMzy said:**
> 

I wrote this tutorial for NTFS partitions, but it should work the same way for FAT partitions: [[COLOR="Blue"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

Being timid about editing things I have little knowlege of, should I just change "NTFS" to "FAT32" or "FAT 32"?

---

### Post by oldfred on 2010-11-07
Its actually vfat.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

one of my old entries:
# Entry for /dev/sdc8 :
UUID=F6A6-705D /media/gdrive vfat user,auto,fmask=0111,dmask=0000 0 0

---

### Post by pbhill on 2010-11-12
I finally edited fstab to include "USB STORAGE", and it now appears in my Places menu, but I still can't write to the disk. What else should I be doing?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid            0  0  
# / was on /dev/sda1 during installation
UUID=50bcd27d-5423-4fe2-a607-4efd25e67879  /            ext3  errors=remount-ro              0  1  
# /home was on /dev/sda5 during installation
UUID=a44c99b8-d52e-40cd-b649-357dcc13da53  /home        ext3  defaults                       0  2  
# /windows was on /dev/sdb1 during installation
UUID=BEEB-B809                             /media/USB Storage  vfat  owner,group=pbhill,users,user  0  1  
# swap was on /dev/sda6 during installation

---

### Post by WorMzy on 2010-11-12
You can't have spaces in mount locations, it messes up the columns; use \040 instead.

Oh and don't use 1 for the last column; only your root partition should have 1. Use 0 or 2. 0 makes fsck skip the partition, 2 makes it check it for errors.

Also, here's a list of all the available options for vfat: [http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt)

If I were you, I'd use the following (assuming you're user 1000) as a starting point:

```
UUID=BEEB-B809 /media/USB\040Storage vfat defaults,uid=1000,gid=1000,umask=000 0 0
```

---

### Post by pbhill on 2010-11-13
Thanks for your reply. I tried the code as you indicated, but it made no difference. I still can't write to this disk. I'm stumped...

I don't understand what would have caused these changes. I've never had any problems with this drive and I've been using it for over three years...

---

