---
title: "Ubuntu 10: an error occurred while mounting /mnt/hgfs"
date: 2010-05-08
forum: General Help
---

### Post by aneuryzma on 2010-05-08
hi,

I'm emulating Ubuntu using VMWare and I've upgraded it to Maverick version.

When I boot the system I get this error (below the Ubuntu logo):

"an error occurred while mounting /mnt/hgfs"

So I have to click S to continue and the the OS seems to work well.

Thanks

---

### Post by kio_http on 2010-05-08
> **aneuryzma said:**
> hi,

I'm emulating Ubuntu using VMWare and I've upgraded it to Maverick version.

When I boot the system I get this error (below the Ubuntu logo):

"an error occurred while mounting /mnt/hgfs"

So I have to click S to continue and the the OS seems to work well.

Thanks

Press ESC while the system boots (when splash appears). You will see some text. Tell us the last line concerned with the mounting error. 

Also when booted open terminal

ALT + F2 when on desktop
```
gnome-terminal
```
In terminal type
```
mount
```
Tell us the output.

Do you have any idea which partition number mounts at /mnt/hgfs?

---

### Post by aneuryzma on 2010-05-08
here you are: [http://dl.dropbox.com/u/72686/mountError.png](http://dl.dropbox.com/u/72686/mountError.png)

---

### Post by ramo5150 on 2010-05-17
I'm having the exact same issue.... 
n e 1 have any ideas on how to fix this?  

Thanks

---

### Post by Milliways on 2010-05-18
I have Ubuntu 10.04 running in a VirtualBox machine.
This has 2 Shared Folders attached (on NTFS partition).

I included the 2 lines in fstab to mount these at boot:-

MilliwaysData   /media/MilliwaysData vboxsf defaults 0 0
temp   /media/temp vboxsf rw 0 0

So far this is identical to what I have done on earlier Ubuntu releases, but Ubuntu 10.04 gives me a warning on boot:-

An error occurred while mounting /media/MilliwaysData
press S to Skip mount or M for Manual Recovery

I note others have reported similar problems.

I removed the error by including the option **noauto**, but **user** does not work for shared folders.

I did see a suggestion that mount could be included in /etc/rc.local

---

### Post by ozviking on 2010-05-20
I have the same problem with my upgrade....have to press s for skip then it boots and works great.
can not access my widows partition. 
here is the reading after the mount command in the terminal

Any one that can help with this problem????



patrick@Super-Beast:~$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/patrick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=patrick)

---

### Post by Milliways on 2010-05-20
I have solved my problem by following the advice at:-

[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

my rc.local now mounts the shares

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t vboxsf -o ro MilliwaysData   /media/MilliwaysData
mount -t vboxsf -o rw temp   /media/temp

exit 0
```

---

