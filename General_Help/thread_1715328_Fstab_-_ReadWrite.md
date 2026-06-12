---
title: "Fstab - Read/Write"
date: 2011-03-26
forum: General Help
---

### Post by JaizEdelmann on 2011-03-26
Hey guys i just finnished setting up my raid and it seems to be working as in inteded running EXT4 with RAID5 4x 2TB (avalible now: 5,4TB so it takes abit off anyway, 

i cant transfer anything to the driveand i think its because that i set something wrong in fstab heres my mount command

```
#raid
/dev/md0        /media/raid     ext4    defaults        0       0

```

Also theres a lost+found folder on the drive should i let that be?

Also is there a command to chk up on the raid so i can see that one of my drive isent broken?

---

### Post by JaizEdelmann on 2011-03-26
/bump

---

### Post by JaizEdelmann on 2011-03-26
Triede mounting like this 
```
from fstab: /dev/md0 /media/raid  auto auto,exec,rw,user 0

```

same results, really need some help :S

```
df -h
```
> /dev/md0              5,4T  186M  5,4T   1% /media/raid


---

### Post by towheedm on 2011-03-27
Firstly, the sixth field in the fstab should be 2 not 0 (the last 0) unless of course you intended to not have the drive cjecked on boot.
The reason you cannot write anything to the drive after mounting is because it's read-only.  You are mounting to a directory that's read-write only by root.

If the drive will be used for user files, then mount it in your home directory.
Change mountpoint in fstab (enter your username for USEWRNAME):
```
#raid
/dev/md0    /home/USERNAME/raid    ext4    defaults    0    2
```Create a directory for the mount point:
```
mkdir ~/raid
```mount the drive from fstab:
```
sudo mount -a
```The ~/raid directory will now be owned by root.  Change owner to you:
```
sudo chown -R $USER:$USER ~/raid
```You now own the raid directory and should be able to read/write to it.

Hope it helps.

---

### Post by JaizEdelmann on 2011-03-27
> **towheedm said:**
> Firstly, the sixth field in the fstab should be 2 not 0 (the last 0) unless of course you intended to not have the drive cjecked on boot.
The reason you cannot write anything to the drive after mounting is because it's read-only.  You are mounting to a directory that's read-write only by root.

If the drive will be used for user files, then mount it in your home directory.
Change mountpoint in fstab (enter your username for USEWRNAME):
```
#raid
/dev/md0    /home/USERNAME/raid    ext4    defaults    0    2
```Create a directory for the mount point:
```
mkdir ~/raid
```mount the drive from fstab:
```
sudo mount -a
```The ~/raid directory will now be owned by root.  Change owner to you:
```
sudo chown -R $USER:$USER ~/raid
```You now own the raid directory and should be able to read/write to it.


This is how i mount my external USB drive and there i have no problems 
LABEL=Alpha /media/mediaStorage1 auto auto,exec,rw,user 0

Hope it helps.

> sudo mount -a
mount: unknown filesystem type 'linux_raid_member' but i can still see the drive

however the chown trick did the works, however what if i want multiple users to writein the filesystem?


This is how i mount my external hdd and i have no write/read problems on that

```
LABEL=Alpha /media/mediaStorage1 auto auto,exec,rw,user 0

```

---

### Post by towheedm on 2011-03-27
> sudo mount -a                                 
mount: unknown filesystem type 'linux_raid_member' but i can still see the driveIs ext4 listed as a known filesystem?  This command should return ext4:
cat /proc/filesystems | grep ext4
 
If nothing is returned, then ext4 is not supported.

One way to give other users write access is to add them to the group specified by the second $USER from the chown command.

> This is how i mount my external USB drive and there i have no problems 
LABEL=Alpha /media/mediaStorage1 auto auto,exec,rw,user 0

What filesystem does the external usb drive use?

---

