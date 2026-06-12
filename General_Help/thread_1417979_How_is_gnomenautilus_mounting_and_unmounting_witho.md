---
title: "How is gnome/nautilus mounting and unmounting without root"
date: 2010-02-28
forum: General Help
---

### Post by narnie on 2010-02-28
Hello,

I'm wondering how usb drives, etc get automounted in gnome now days. Thought it might be fusermount, but no. Gnome-mount is not installed. Perhaps it is via HAL or udev, but what commands control it?

I would like to unmount certain volumes via the command line, but without having root privileges as gnome is doing by clicking in nautilus. I would like to do the equivalent from the command line.

Are there any command lines commands that will allow me to do this (not talking about pmount which is not installed)?

Also, is there a way to prevent automounting of just certain devices, but not all? I have a USB with 7 different things on it (a "built-in" CD for some reason for windoz users, the original NTFS, and 5 linux partitions). I really only want one of the linux partitions (an XFS for DVD isos) to automount but not all the others. I would like not to have to disable ALL automounting as in:```


$ gconftool-2 -s /apps/nautilus/preferences/media_automount --type=bool false
$ gconftool-2 -s /apps/nautilus/preferences/media_automount_open --type=bool false

```

With thanks,
Narnie

---

### Post by narnie on 2010-02-28
Problem is 1/2 solved. Did some playing around and found gvfs info leading me to gvfs-mount.
Listing the mount gives me these results:

```
woodnt@toshiba-laptop /dev $ gvfs-mount -l
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(1): 499 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): DATA
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
  Volume(1): Linux3
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
  Volume(2): Linux2
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
  Volume(3): Linux4
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
  Volume(4): Linux1
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
Drive(2): CD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): WD SmartWare
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
Drive(3): 500 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): TI100343V0F
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
```I can mount my partition from the command line with:

```
woodnt@toshiba-laptop /dev $ gvfs-mount -d /dev/sdb9

(gvfs-mount:27658): GLib-GIO-CRITICAL **: g_mount_get_root: assertion `G_IS_MOUNT (mount)' failed

(gvfs-mount:27658): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed
Mounted /dev/sdb9 at (null)

(gvfs-mount:27658): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gvfs-mount:27658): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```Mount gives:
```

woodnt@toshiba-laptop /dev $ mount|grep /dev/sdb9
/dev/sdb9 on /media/DATA type xfs (rw,nosuid,nodev,uhelper=devkit)
```I can also successfully unmount via:
```

woodnt@toshiba-laptop /dev $ gvfs-mount -u /media/DATA/
woodnt@toshiba-laptop /dev $ mount|grep /dev/sdb9
woodnt@toshiba-laptop /dev $
```So, for the most current Gnome'rs out there, this is how it is done and how scripting can manage it. BTW, somehow, fuser is involves as can be seen with:

```
woodnt@toshiba-laptop /dev $ mount|grep fuse
none on /sys/fs/fuse/connections type fusectl (rw)
gvfs-fuse-daemon on /home/woodnt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=woodnt)

```Now, how does one modify udev rules or hal policies to prevent mounting of all partitions except the one you want. Feel free to chime in, or I'll post if I find the answer for future posterity.

Narnie

---

### Post by narnie on 2010-02-28
BTW, I know that I could always hardcode something like:

```
/dev/sda5       /media/LINUX1    ext3    defaults,user,noauto    0   0

```

However, I don't want to have to "assign" a mountpoint like /media/data to it.

gvfs-mount automatically creates a mountpoint, then mounts the partition to that sight. It cleans up after itself well, too. It will unmount the partition and delete the mountpoint. Otherwise, for all my drives and partitions, I have to leave mountpoints with the volume names like /media/DATA, /media/Linux1, /media/Linux2, etc for each volume label of each partition of all the USB hard drives I have (quite a fiew). That seems like a waste.

Hence, my desire to go a step (or two) deeper than just a "simple" /etc/fstab entry that commits me to have a mountpoint directory already made and static, rather than dynamic.

That, plus I just want to learn (udev rulz or HAL rulz, or whatever).

Thanks,
Narnie

---

### Post by n0_mad on 2010-04-17
Is it possible to mount dive knowing only its label? Like in gnome-mount?

---

