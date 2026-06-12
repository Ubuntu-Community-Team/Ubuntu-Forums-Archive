---
title: "Can I use the rest of my harddrive without reinstalling?"
date: 2010-01-07
forum: General Help
---

### Post by CheshireMac on 2010-01-07
Hey folks. I thought I installed properly, but once again I've made a mistake. I'm trying to make use of the 114 gb I didn't assign as file system space, but I can't seem to access it or write to it. I've officially run out of space in my file system and I've got a lot to do still. Any thoughts on how to make the unused partition accessable?

---

### Post by michy99 on 2010-01-07
You can either expand the existing partition into the free space, or create one or more new partitions and mount them for use. First I would be sure that your system partition is big enough. What is the output of```
sudo fdisk -l
```

---

### Post by louieb on 2010-01-07
Need a look at the partition table. Please post the output of
```
sudo fdisk -l
```lowercase L at the end

---

### Post by audiomick on 2010-01-07
How do you know you are "officially out of space" ? Not that I don't believe you, I'd just be interested in knowing how you found out.

---

### Post by CheshireMac on 2010-01-07
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         764     6136798+  12  Compaq diagnostics
/dev/sda3             765       19457   150151522+   5  Extended
/dev/sda5           19436       19457      176683+   7  HPFS/NTFS
/dev/sda6             765        2631    14996614+  83  Linux
/dev/sda7            2632        4543    15358108+   7  HPFS/NTFS
/dev/sda8            4544       19435   119619958+  83  Linux

```
That's it.

---

### Post by michy99 on 2010-01-07
> **louieb said:**
> Need a look at the partition table. Please post the output of
```
sudo fdisk -1
```lowercase L at the end

Yes, it should be a lowercase L at the end, but in your code box, you put the number 1!

---

### Post by michy99 on 2010-01-07
How about the output of these?```
mount
cat /etc/fstab
```

---

### Post by CheshireMac on 2010-01-07
```
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mac/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mac)
mac@mac:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=97acee98-ae33-4279-b6ec-9de3f7189811 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=752eb8fa-c9fe-442e-b005-3153607a022b none            swap    sw              0       0

```
Thanks for the help by the way.

---

### Post by unmole on 2010-01-07
Probably the dumbest suggestion that you will get.
-Backup your /home
-Boot into live cd
-Resize what was previously your /home to include your extra 114 gigs aswell
-mark your new partition /home


See this for more details [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by audiomick on 2010-01-07
> # swap was on /dev/sda5 during installation

> /dev/sda5           19436       19457      176683+   7  HPFS/NTFS

What happened here?

---

### Post by CheshireMac on 2010-01-07
Any way I can do it without going to a live disc?

---

### Post by michy99 on 2010-01-07
All of your "missing" space seems to be on /dev/sda8, so you should be able to mount it and use it. First, make a mount point. I am calling it DISK, but you can call it something else if you want.```
sudo mkdir /media/DISK
```Now set the permissions. Use your actual username where it says YOUR_USER_NAME```
sudo chown YOUR_USER_NAME:users /media/DISK
```Open fstab for editing.```
gksudo gedit /etc/fstab
```Add this line:```
/dev/sda8 /media/DISK ext3 defaults 0 2
```Save and exit. Now see if it mounts.```
sudo mount -a
```If it works, then it will automatically mount whenever you boot.

---

### Post by CheshireMac on 2010-01-07
After that last bit, I still don't have permissions.

---

### Post by michy99 on 2010-01-07
What do you get for```
ls -l /media
```

---

### Post by louieb on 2010-01-07
> **CheshireMac said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         764     6136798+  12  Compaq diagnostics
/dev/sda3             765       19457   150151522+   5  Extended
/dev/sda6             765        2631    14996614+  83  Linux
/dev/sda7            2632        4543    15358108+   7  HPFS/NTFS
/dev/sda8            4544       19435   119619958+  83  Linux
/dev/sda5           19436       19457      176683+   7  HPFS/NTFS

```That's it.

Rearranged the output in start order.  anything you want to keep in sda7 or sda8 or sda5? 

> I've officially run out of space in my file system 
Post the output of 
```
df -h
```
> Any way I can do it without going to a live disc? 	
Resizing partitions should be done using a Live CD.  
> After that last bit, I still don't have permissions. 	
michy99's suggestion should work - do post the ls -l /media output he asked for. - 

> **michy99 said:**
> Yes, it should be a lowercase L at the end, but in your code box, you put the number 1!

:D Fat fingers or brain fart - take your pick. .

---

