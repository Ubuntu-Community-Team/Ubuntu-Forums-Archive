---
title: "mount WINDOWS Filesystem-device automatically when ubuntu start up"
date: 2011-03-06
forum: General Help
---

### Post by ubu@ on 2011-03-06
Hi,

this is my story: :popcorn:
When starting my Ubuntu, the state of Filesystem device is **unmount**. it means that all the application that are using "windows" files, not working well. for example, all of my songs are located in this device: FIlesystem (all windows-OS files), so Rhythmbox's list is empty. listing to music requiring 2 steps,
1) Places -> click on "125 GB Filesystem" drive.
2) Rhythmbox -> click on "play" 

My question is, how can I make step1 to happen automatically?
I Know there is command called "mount" (including it in some script that running in startup-applications can solve the problem), but i try all the version of the command and I get errors. so there is someone that know this command ("mount") from childhood?

Thanks,
Ubu.

---

### Post by TeoBigusGeekus on 2011-03-06
Mount the partition and post us the output of
```
sudo fdisk -l
```
```
mount
```
```
sudo blkid
```
and the contents of your fstab file
```
gksu gedit /etc/fstab
```
Don't forget to mention which is the partition you want mounted on startup.

---

### Post by lithopsian on 2011-03-06
Use the mount command to test mounting the windows filesystem, then put an entry in /etc/fstab so that it is mounted automatically.

You will need to know the device name (or UUID) of the disk and the filesystem type.  You will also need a mountpoint within the Linux filesystem.  Typically this would be something like /mount/windows.  The command will be something like:
```

sudo mount -t ntfs /dev/sdb1 /mount/windows

```If it is an NTFS disk then you will have to make sure you have the ntfs_3g package and will probably want to specify some additional options, but this command will at least  test the mount is possible.

---

### Post by hallbrian on 2011-03-06
You can use software to do it for you, mount all/some partition at startup.

If you go for the automatic configuration, install ntfs-config

```
sudo apt-get install ntfs-config
```

Now, it's rather easy. Just launch ntfs-config via the menu (in system tools) or via the terminal

```
gksu ntfs-config
```

---

### Post by ubu@ on 2011-03-06
first, your are really fast!!! if i knew this place, some years of fighting with "man" command were spared...
thanks for the attention.

the output for "sudo fdisk -l" after mounting is:
```
 
 Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7153ad3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       15392   122098688    7  HPFS/NTFS
/dev/sda3           15392       30401   120559948    7  HPFS/NTFS

```

output for "mount":
```

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ed)
/dev/sda2 on /media/7EFAEF2FFAEEE1FF type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

output for "sudo blkid"
```

/dev/loop0: UUID="ee93b0be-e2c0-445f-827d-e79994cd89f9" TYPE="ext4" 
/dev/sda1: LABEL="WinRE" UUID="5CEE9CD7EE9CAAB2" TYPE="ntfs" 
/dev/sda2: UUID="7EFAEF2FFAEEE1FF" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="08AEA3B1AEA395AA" TYPE="ntfs" 

```

output for "gksu gedit /etc/fstab"
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

---

### Post by TeoBigusGeekus on 2011-03-06
Dedacted.

---

### Post by lithopsian on 2011-03-06
You have two windows drives?

In /etc/fstab, put:
```
/dev/sda2     /media/windows1     ntfs-3g     defaults   0    0
/dev/sda3     /media/windows2     ntfs-3g     defaults   0    0
```

You might want to add more options where it says defaults.  a locale, a charset, and maybe umask.  You can also replace /dev/sda2 and /dev/sda3 with the UUID (start the line with "UUID=") so that it keeps working even if your driver numbers get shuffled about,

---

### Post by ubu@ on 2011-03-06
thank you [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094")  for the effort (i learn some using these commands)
i used **hallbrian **2 lines for installing "ntfs-config"and it work perfectly after rebooting.

too good...

thank you all!!!@##:guitar:

---

