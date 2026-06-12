---
title: "Change mountpoint for external hard drive"
date: 2009-11-28
forum: General Help
---

### Post by Jim_in_Germany on 2009-11-28
Hi,
I have an external usb hard drive containing my music.
Currently when I turn it on it is mounted under /media/music.
I would like to change that so that in the future it is mounted under /home/jim/Music instead.
Could someone give me a couple of pointers as to how I would go about doing that.
Thanks in advance

---

### Post by scragar on 2009-11-28
```
gksu gedit /etc/fstab
```
Change where it says /media/music to read /home/jim/Music

---

### Post by blueridgedog on 2009-11-28
You would put an entry in to your /etc/fstab file for the mount.  If you tell me more about the drive (what device it is and how it is formated), I can help you put the entry you need into your fstab file.

To get the information needed you can (with the drive plugged in and mounted) use the following commands:

```
mount
```

and 

```
sudo fdisk -l
```

Post the output of those commands and we can go to the next step.

---

### Post by blueridgedog on 2009-11-28
> **scragar said:**
> 
Change where it says /media/music to read /home/jim/Music

Since it is automaounted in the /media tree, there probably won't be an entry in fstab for it.

---

### Post by Jim_in_Germany on 2009-11-28
Hi,

Thanks for the replies. 
Here are the outputs you asked for blueridgedog:

mount:
```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
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
/dev/sda3 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
none on /proc/bus/usb type usbfs (rw,devgid=121,devmode=664)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jim)
/dev/sdb5 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x649c5b15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20060   161131918+  83  Linux
/dev/sda2           20061       21640    12691350    5  Extended
/dev/sda3           21641       60801   314560732+   7  HPFS/NTFS
/dev/sda5           20061       21640    12691318+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd86768c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156288000    f  W95 Ext'd (LBA)
/dev/sdb5               1       19458   156286976    7  HPFS/NTFS
```

---

### Post by blueridgedog on 2009-11-28
It appears then that you disk is sdb5 and is formated for the windows file system:

```
/dev/sdb5               1       19458   156286976    7  HPFS/NTFS
```

You state that you want to mount the drive at /home/jim/Music.  Fist, move any files out of the existing folder /home/jim/Music, as you will use that as a mount point.  You can use nautilus to move the files.

Second, unmount the drive from the existing mount points:

```
sudo umount /dev/sdb5
```

Your user ID on the system is probably 1000, but it is easy to check:

```
cat /etc/passwd | grep jim
```

If your user ID is anything other than 1000, change it in the mount option below.

Edit /ect/fstab to mount the drive in the new location
```

gksudo gedit /etc/fstab
```

Add The following line:

```
/dev/sdb5 /home/jim/Music ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1

```

Save the file then restart to have the new /etc/fstab file read.

---

### Post by Jim_in_Germany on 2009-11-28
Hi,
Thanks very much for your help.
I followed your instructions and everything worked fine, except when I switch on my usb drive I get the error message "mount: only root can mount /dev/sdb5 on /home/jim/Music"
Stragely, the drive still gets mounted and appears where it should (ie. /home/jim/Music".)
I also get the same error if I try to unmount the drive as jim.
Any ideas?

---

### Post by blueridgedog on 2009-11-28
When a drive is mounted via fstab, only root can unmount it, so prior to unplugging it, you will need to:

```
sudo umount /dev/sdb5
```

If the drive is plugged in while booting, you should not get the error.  The only way I have seen to user mount and unmount drives is to use the automatic feature, which puts it in the /media tree.  You could use that and simply make you /home/jim/Music directory a link to the /media/Music directory.  I can help with that if you want to back out of the current mounting.  I mount my drives in my home directory and just use sudo to unmount them if needed.

---

### Post by Jim_in_Germany on 2009-11-29
Hi,
Unfortunately I share the drive between computers, plus I try to be as power concious as possible (i.e. it is better to just turn the drive on when I need it), therefore the drive is not normally mounted at boot.

The entry in fstab seems to mean that on boot an entry is created for /home/jim/Music (which if the drive is turned off, obviously won't work). This appears under places, below my documents folder.

If I then turn the drive on, a second entry is created in places, a bit further down, below computer. Both entries will then work and point to /home/jim/Music

I have been doing a bit of research since last night and it seems to point to the fact that the gvfs-fuse-daemon is responsible for mounting usb drives at run time. Is there any fuse configuration file I could alter to achieve my goal?
I tried looking at /etc/fuse.conf, but that didn't help any.

You are quite right that an easy solution to this situation would be to simlink the drive from /media/Music to /home/jim/Music, but I read that it should be possible to plug various drives in to any preferred point in the file system, so I am well curious as to how this works. (if I understood this wrong then anybody please feel free to correct me).

Thanks for your help and time so far.

---

### Post by blueridgedog on 2009-11-29
I did a search and could not find how to configure where gvfs mounts files.  I have typically have not used gvfs as I simply want my files "where I want them".  However, I do use it for flash drives and similar removable media.  I will keep looking as I would like to know how to configure gvfs.

---

### Post by Jim_in_Germany on 2009-11-30
Hi,

I've spent the last day or so Googling this issue, and from what I can tell, it doesn't seem to be possible to change gvfs's default mountpoint of /media for USB drives.

If you ever find out anything to the contrary I would be very obliged if you could let me know.

Thanks again.

---

