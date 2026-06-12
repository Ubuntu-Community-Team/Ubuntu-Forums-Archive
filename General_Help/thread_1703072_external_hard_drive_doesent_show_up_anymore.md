---
title: "external hard drive doesent show up anymore"
date: 2011-03-08
forum: General Help
---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-08
hi i just installed ubuntu on a new computer and first time i tried to connect my external hard drive it showed up, 
now it doesent show up anymore even how many times i have tried to restart computer and the external drive many times, i have also try to take the usb cable out and in too

when i try the command lsusb, it finds it:
Bus 001 Device 006: ID 059b:0370 Iomega Corp.
wich is my external drive...

---

### Post by blueridgedog on 2011-03-08
With the drive plugged in, what is the output of 

```
sudo fdisk -l
```

(note that is a lower case "L")

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-08
```
Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f334f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43013   345496576   83  Linux
/dev/sda2           43013       43778     6141953    5  Extended
/dev/sda5           43013       43778     6141952   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

```

---

### Post by blueridgedog on 2011-03-08
I assume sdb is the external drive (you have only one internal drive?).

What is the output of the command

```
mount
```

?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-08
> **blueridgedog said:**
> I assume sdb is the external drive (you have only one internal drive?).

What is the output of the command

```
mount
```?
internal drive means HD that is in my computer yes? yes only one, is that one at 360 gb
the other one in that list with 1000 gb is my external hd, but it doesent show up on the desktop or computer

here:
> /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/home/kristoffer/.Private on /home/kristoffer type ecryptfs (ecryptfs_sig=3e377ed772aedb3b,ecryptfs_fnek_sig=1e44d88a472175a2,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/kristoffer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kristoffer)


---

### Post by blueridgedog on 2011-03-08
Ok, so the external drive is not auto mounting.  I can't fix that as I don't use auto mounting in my system, but I can show you have to mount it manually.  If you don't want a manual solution, another forum member may offer a automount solution.

To mount it manually each time:

Make a directory for the drive to be mounted to:

(change USER to your user account and "files" to whatever suits you...do so throughout the instructions)

```
mkdir /home/USER/files

```

Then mount the drive:

sudo mount /dev/sdb1 /home/USER/files

To have it automatically mounted when you boot your PC:

Make a directory for the drive to be mounted to:

```
mkdir /home/USER/files

```

Your user ID on the system is probably 1000, but it is easy to check:

```
cat /etc/passwd | grep USER
```

If your user ID is anything other than 1000, change it in the mount option below.

Edit the file /ect/fstab to mount the drives in the new locations, making a backup first:
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

Add The following lines:

```
/dev/sdb1 /home/USER/files ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1

```

Save the file then mount them with
```

sudo mount /home/USER/files
```

Remember to change USER everywhere you see it and also you can adjust the mount point as you want, but make certain you own the mount point.  If you make a mount point in another part of the system, give yourself ownership with:

```
sudo chown USER:USER /path/to/new/mountpoint
```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-08
> **blueridgedog said:**
> Ok, so the external drive is not auto mounting.  I can't fix that as I don't use auto mounting in my system, but I can show you have to mount it manually.  If you don't want a manual solution, another forum member may offer a automount solution.

To mount it manually each time:

Make a directory for the drive to be mounted to:

(change USER to your user account and "files" to whatever suits you...do so throughout the instructions)

```
mkdir /home/USER/files

```Then mount the drive:

sudo mount /dev/sdb1 /home/USER/files


thanks this worked, but it has not the orginal device name but "files" but doesent matter ):P

---

### Post by yuler on 2011-03-08
MountManager is a GUI for managing device mounts.  Being a Ubuntu newbie, I found it quicker to get the job done than wading through help files.

```

sudo apt-get install mountmanager

```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-10
i have another question: curently i am using the first 2 commands u gave me everytime i reboot my computer i have to do them again..
> (change USER to your user account and "files" to whatever suits you...do so throughout the instructions)

     Code:
     mkdir /home/USER/files 
Then mount the drive:

sudo mount /dev/sdb1 /home/USER/filesbut if i do the others u said, if i do them, will the external hd show up everytime after i do it?

---

