---
title: "No more space on my usb disk but there is."
date: 2011-03-24
forum: General Help
---

### Post by colobix on 2011-03-24
Hey. This is one of the biggest frustrations I have seen in ubuntu so far. Until now I have just formated the disks, but it's frustrating since I need the files on the disk and I bet there's an easier way out. I tried to physically delete the .trash folder in the flash disk but that didn't work either.
So, what do I do?

---

### Post by Bucky Ball on 2011-03-24
Delete the trash on your hard drive. It sounds crazy but that is the way it is if you delete the external device. For some reason it deletes to the system trash and unless you delete it from there, whenever you plug in it shows the device as full. ;)

---

### Post by colobix on 2011-03-24
I've already tried that, and I still get the error when I try to move files over to the flash disk.
I have deleted the trash in my home folder, root and the flash disk. So, what now?

---

### Post by vanadium on 2011-03-24
My guess is that the file system of your USB is damaged. There are probably a lot of "lost clusters", i.e. clusters marked as used, but with no file pointing to them. Check the file system.

---

### Post by colobix on 2011-03-24
what do you mean check the file system? for what? It's fat32 and that's all I know.

---

### Post by Another Monkey on 2011-03-24
fat32?  And what size are the files?  there are limits to what fat32 can handle and you may be exceeding the files size.
There may be a limit on volume size/number of folders/files but I can't recall.
It's a shame that ext4 isn't more portable.

---

### Post by vanadium on 2011-03-24
> **colobix said:**
> what do you mean check the file system? for what? It's fat32 and that's all I know.
File systems need to be checked regularly for consistency. Internal drives are checked automatically during startup. External drives never get checked.

You can check and repair a fat drive in linux with the command "dosfsck". You first need to determine the device name:
```

sudo blkid

```
Among the partitions, your usb stick will be listed. The devicename is the very first part of the line and looks like: /dev/sda1, or /dev/sdb

The USB must be unmounted before you check it:

```

sudo umount <device>

```
where <device> is the devicename you found out before.
Then comes the checking with repair (option -a for "automatic")
```

sudo dosfsck -a <devicename>

```
This is similar as "checkdisk /f a:" under MS Windows.

---

### Post by colobix on 2011-03-24
ok. I unmounted it and pasted in that command.
The flash disk came up again but I can still not put in any files.
I have never ran into this problem in windows btw
Aren't there any problems I can use for this? I checked synaptic but no luck.
EDIT: The disk's folder name is 1CEE-E4A8, and the device name is sda3.
At least it was. I think it's something else now.
Also, I unmounted it the normal way (right click > unmount) since it goes faster than using the terminal.
I also prefer to do things that way. Makes me feel less nerdy.

---

### Post by vanadium on 2011-03-24
> **colobix said:**
> EDIT: The disk's folder name is 1CEE-E4A8, and the device name is sda3.
This does not look like a partition name for an USB. It is the third partition of your primary hard disk.

---

### Post by colobix on 2011-03-24
I don't even know, ok?
So how do I fix this, and are there any software to do this with?
We are talking about my mp3 player here and that's why I don't wanna format it. There are software and stuff there I don't think will work afterwards

---

### Post by vanadium on 2011-03-25
Insert the mp3 player, then post the output of the commands
```

mount
sudo blkid

```

---

### Post by colobix on 2011-03-25
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
/dev/sda1 on /media/Reservert_av_systemet type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/EF9C-3143 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc on /media/1CEE-E4A8 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
chris@chris-Aspire-R3600:~$ sudo blkid
/dev/sda1: LABEL="Reservert av systemet" UUID="D43004B430049F9A" TYPE="ntfs" 
/dev/sda2: UUID="FE5C091E5C08D377" TYPE="ntfs" 
/dev/sda3: UUID="36680C9B680C5C4D" TYPE="ntfs" 
/dev/sda5: UUID="38928ad8-5980-4ea7-af75-90688566fd3c" TYPE="ext4" 
/dev/sda6: UUID="80105796-f843-4a24-9e10-d5295e594b8c" TYPE="swap" 
/dev/sdb1: UUID="EF9C-3143" TYPE="vfat" 
/dev/sdc: UUID="1CEE-E4A8" TYPE="vfat"

---

### Post by vanadium on 2011-03-25
All right, now I have a new problem. You have two fat drives attached on your computer, and now I can not know which one is your USB.

Let's assume its the /dev/sdc.

```

sudo umount /dev/sdc
sudo dosfsck -a /dev/sdc

```
When dosfsck has finished, unplug the drive and plug it back in.

With option -a, repair would go automatically. Lost clusters will be converted to files with strange names. You will need to delete these, and after that the trash, to effectively free the space they took.

To check your other vfat volume, replace /dev/sdc by /dev/sdb1 in the above commands.

If in doubts, post all output of the commands here.

---

### Post by colobix on 2011-03-25
ok here:

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
/dev/sda1 on /media/Reservert_av_systemet type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc on /media/1CEE-E4A8 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
chris@chris-Aspire-R3600:~$ sudo blkid
[sudo] password for chris: 
/dev/sda1: LABEL="Reservert av systemet" UUID="D43004B430049F9A" TYPE="ntfs" 
/dev/sda2: UUID="FE5C091E5C08D377" TYPE="ntfs" 
/dev/sda3: UUID="36680C9B680C5C4D" TYPE="ntfs" 
/dev/sda5: UUID="38928ad8-5980-4ea7-af75-90688566fd3c" TYPE="ext4" 
/dev/sda6: UUID="80105796-f843-4a24-9e10-d5295e594b8c" TYPE="swap" 
/dev/sdc: UUID="1CEE-E4A8" TYPE="vfat" 

I think it's sda3 but Im not sure.

---

### Post by vanadium on 2011-03-25
My previous post already told yu how to proceed.

---

### Post by coldraven on 2011-03-25
Try this, open System>Admin>Disk Utility
Click on your USB stick in the left window.
On the bottom left click "Unmount"
Below that button click "Check Filesystem"
Anything happen?

---

### Post by colobix on 2011-03-25
But I don't know which one is the flash disk.
I took a chance and tried it sdc.
But I still get the error saying it's full.

@coldraven, thanks, I tried what you suggested but after the test and it says "file system is clean", I still can't add files to the disk

---

### Post by colobix on 2011-03-28
bump.

---

