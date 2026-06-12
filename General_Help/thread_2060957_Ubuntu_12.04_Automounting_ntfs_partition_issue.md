---
title: "Ubuntu 12.04 Automounting ntfs partition issue"
date: 2012-09-21
forum: General Help
---

### Post by kasunt on 2012-09-21
Hi folks,

Ive looked everywhere to fix this problem but I cant seem to figure out why its doing this. I have the following /etc/fstab entry to mount a ntfs partition using ntfs-3g.

```
UUID=01CD842715EC2180   /media/mediahd02        ntfs    defaults,user,noexec,uid=1000,gid=1000,dmask=007,fmask=117      0       2
```

The volume label for this partition is "MEDIA02"

So I have had no problems with the fstab mounting. The problem however is that it automounts again using MEDIA02 label. I'm not sure automounting is the right term for this as its just an empty directory. Deleting this directory and rebooting is causing it to appear again.

If I list /media I see both MEDIA02 & mediahd02

Can someone shed some light as to why its doing this ?

---

### Post by oldfred on 2012-09-21
Mounts in /home & /media show twice like you have found out.

My work around is to mount in /mnt and link folders from the shared data partition back into /home.

Another way that I have not tried. Not sure if still valid with current version.

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)


One of the users here that knows mounting very well (Morbius1) suggests these settings for NTFS.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

You want the last two should both be 0 for NTFS. It is:
# The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.

You cannot run chkdsk from Linux on NTFS but need to use Windows to run chkdsk periodically. Ubuntu runs its fsck every 40 or 60 reboots on those partitions set with 1 or 2.

---

### Post by kasunt on 2012-09-22
ok classic newbie error.

I created this script /etc/udev/rules.d/11-media-by-label-auto-mount.rules during setting up of my system which is what was causing this issue. Its suppose to be automounting usb disks for my htpc while ignoring system disks.

Contents of the script:

 ```
   KERNEL!="sd[b-z][0-9]", GOTO="media_by_label_auto_mount_end"
    
    # Import FS infos
    IMPORT{program}="/sbin/blkid -o udev -p %N"
    
    # Get a label if present, otherwise specify one
    ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
    ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"
    
    # Global mount options
    ACTION=="add", ENV{mount_options}="relatime"
    # Filesystem-specific mount options
    ACTION=="add", ENV{ID_FS_TYPE}=="vfat|ntfs", ENV{mount_options}="$env{mount_options},utf8,gid=100,umask=002"
    
    # Mount the device
    ACTION=="add", RUN+="/bin/mkdir -p /media/%E{dir_name}", RUN+="/bin/mount -o $env{mount_options} /dev/%k /media/%E{dir_name}"
    
    # Clean up after removal
    ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l /media/%E{dir_name}", RUN+="/bin/rmdir /media/%E{dir_name}"
    
    # Exit
    LABEL="media_by_label_auto_mount_end"

```
However my disk which I'm having problems with is /dev/sdb1 and hence this script takes over. I have since modified it to ignore sdb.

---

