---
title: "iPhone won't mount anymore"
date: 2011-03-08
forum: General Help
---

### Post by steveneddy on 2011-03-08
I have an iPhone 3GS that was mounting a couple of weeks ago but now does not.

Looking in /mnt I see a folder for the phone but the folder is empty.

Phone is listed when I perform 

```
lsusb
```

 in terminal.

Here is output of mount

```

steveneddy@machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/steveneddy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steveneddy)

```

I do not know what else to do.

Also of note - I took a couple of photos off of the phone at work using an XP machine - just browsing the folder in Explorer, no iTunes.

I believe this is where the trouble started.

Any help appreciated.

I will monitor this thread the best I can through the week and weekend - I will do my best to post any terminal output or commands at the earliest possible opportunity.

Thanks again.

---

### Post by steveneddy on 2011-03-20
After much thought - I believe my issue actually started when I plugged the iPhone into a Windows machine at work to get a video or pic off of the phone.

I have tried plugging the phone back into the Windows machine to see if it mounts and try unmounting the phone like a USB drive, but I never saw that option.

Otherwise the phone works well and I was even able to plug it into the Windows 7 install I have on a VM and update to version 4.3 - but I cannot get the iPhone to mount on my Ubuntu box.

---

