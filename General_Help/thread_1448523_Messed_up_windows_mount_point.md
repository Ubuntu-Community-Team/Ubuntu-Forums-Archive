---
title: "Messed up windows mount point?"
date: 2010-04-06
forum: General Help
---

### Post by palz2015 on 2010-04-06
I just installed MountManager to set my Windows partition (/dev/sda1, NTFS) with a mountpoint of /windows. I did this, but now the drive Windows doesn't show up in computer. What should I do? Can I reset the original mount point (/media/windows)?

Edit: Just moved the mountpoint to /mnt/windows. Doesn't work :(

---

### Post by rbc on 2010-04-06
Just a thought, but is this Windows partition mounted while you are trying to change the mountpoint. If so, try unmounting it first. If that doesn’t work, open terminal, type three commands consecutively, then post back with the results:
mount
sudo blkid –c /dev/null
gedit /etc/fstab

---

### Post by palz2015 on 2010-04-06
Set it back to /windows when unmounted and that doesn't help.

mount:
```
mistic@LinuxPC:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mistic/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mistic)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
mistic@LinuxPC:~$ 



```sudo blkid –c /dev/null:
Nothing;
```

mistic@LinuxPC:~$ sudo blkid –c /dev/null
[sudo] password for mistic: 
mistic@LinuxPC:~$

```

gedit fstab:

/dev/sda2    /    ext3    defaults    0    1
/dev/sda3    swap    swap    sw    0    0
/dev/sda1    /windows    ntfs-3g    defaults    0    0

Still not working, :popcorn:

---

### Post by rbc on 2010-04-06
So it’s getting mounted, it’s just not showing up where you want?
OK. After unmounting Windows and changing the mount point back to /media/windows, open terminal and type:
sudo mount -a

---

### Post by palz2015 on 2010-04-07
Thanks. Any idea how to keep it mounted at /windows but have it show up in computer and all?

---

