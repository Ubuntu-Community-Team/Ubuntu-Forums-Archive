---
title: "Windows partition unwritable from Ubuntu after defragmentation"
date: 2009-09-28
forum: General Help
---

### Post by svivian on 2009-09-28
I have a dual boot system with Vista and Ubuntu. I use Ubuntu 99% of the time and have the Windows partition mounted for read/write.

I just ran Diskeeper 2008 while in Vista to "clean up" the disk a bit. It's a large partition of about 250 GB, but it "only" had around 12% free space. I ran a boot time defrag as well as defragging the C: drive a few times. 

However, back in Ubuntu I'm no longer able to write to the Windows partition. Trying to create a file gives the error:

> Error opening file '/media/OS/Users/Scott/Videos/new file': Input/output error

Running mount on Ubuntu shows the partition is writeable, I think:

```
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

Any ideas what gives?

---

### Post by svivian on 2009-09-28
bump :D

---

### Post by svivian on 2009-09-29
Here is my /etc/fstab if it helps. The last line is the Windows partition.

```
proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=dc57d1f6-e720-47ee-86e2-c24fa4e24dff / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=fdf33781-b661-4216-a2a2-6fe61e27f399 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/OS ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

---

### Post by langi280179 on 2009-09-29
Manually unmounting / mounting shows any messages in terminal?

---

### Post by wojox on 2009-09-29
Post the results of 

```
mount
```

---

### Post by svivian on 2009-09-29
Results of mount:

```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/scott/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=scott)
```

The line "/dev/sda3 on /media/OS ..." is the Windows partition.

---

### Post by svivian on 2009-09-29
> **langi280179 said:**
> Manually unmounting / mounting shows any messages in terminal?

Nope. No messages in terminal, but I still have the same "Input/Output error" when trying to write to it.

I was playing around with sharing in Vista the other day, could that have anything to do with it? Every time I downloaded anything to the HD it would show up as shared in Vista, so I "unshared" a bunch of stuff yesterday.

I can still access it fine in Vista though, and previously I could read/write to "non-shared" parts in Ubuntu.

---

### Post by svivian on 2009-09-29
I ran "chkdsk" from Windows, and it's seemed to fix the problem. Something about "invalid security IDs", whatever that is....

---

