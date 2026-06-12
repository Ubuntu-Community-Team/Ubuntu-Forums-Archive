---
title: "Live CD: do not want to mount root fs"
date: 2011-03-30
forum: General Help
---

### Post by tdennist on 2011-03-30
Hello,

Recently my laptop running Ubuntu 10.10 shut down uncleanly, and now refuses to boot.

When I boot from a Live CD, dmesg shows me the following messages:

```

EXT4-fs (sda6): INFO: recovery required on readonly filesystem
EXT4-fs (sda6): write access will be enabled during recovery
EXT4-fs warning (device sda6): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
EXT4-fs warning (device sda6): ext4_clear_journal_err: Marking fs in need of filesystem check
BUG: unable to handle kernel paging request at 02745000
...

```

And a stack trace is produced (which I can paste here if it is informative).

Note that /dev/sda6 is my root partition.

Then, when I try to run a manual fsck once the live cd has booted:

```

# mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-

1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)
# fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?

```

So, I can't boot because the filesystem is needs repairing, but I can't repair the filesystem because the live cd 

insists on trying to mount it beforehand.

Any ideas?

---

### Post by davidmohammed on 2011-03-30
You have mounted the hard-drive from the live CD.

Suggest just do a fsck directly on /dev/sda6

i.e.

boot from live cd

open a terminal and type



sudo fsck /dev/sda6

if the live CD continues to mount the partition then force a unmount

sudo umount /dev/sda6

---

### Post by tdennist on 2011-03-30
Hello,

Thank you for your reply.  In my first message, I stated that I was booting from a Live CD and trying the fsck directly. That didn't work.  And if I try to unmount:

(# designates a root prompt)
```

# umount /dev/sda6
umount: /dev/sda6: not mounted

```

So I don't know what to make of this situation. Is there a boot option in the live CD to prevent it from mounting any physical partitions?  I suppose I could just disconnect the HDD before booting, but that is difficult in a laptop.

---

### Post by davidmohammed on 2011-03-30
hmmm - have found various suggestions [here]("http://ubuntuforums.org/showthread.php?t=1518426").  Its not a long read, but has some useful tips.

---

### Post by tdennist on 2011-04-02
Hello,

This is becoming problematic.  I tried hitting with a bigger hammer: reinstalling Ubuntu on that partition.  However, since the Live CD smartly tries to mount the buggy partition on boot, I cannot do a normal install either.  The partition manager just hangs indefinitely while it tries to figure out what to do with the buggy partition.

Is there a way to *stop mounting* partitions during boot?  Possibly a boot option that says no-mount=/dev/sda6 or something to that effect.

I'm still unsure what I will do if I succeed in booting into a live CD without mounting that filesystem, but I'm hoping either a manual fsck will work, or at the very least a reformat.

I don't believe this is a hardware problem, because my windows partition on the same physical disk is unharmed.

---

### Post by tdennist on 2011-04-02
Fixed by booting into an old kernel. The older kernel did not exhibit the bug, and was able to run fsck and repair the errors.

For posterity:
buggy kernel: 2.6.32-30-generic
good kernel:  2.6.32-21-generic

---

### Post by GrzegorzWo on 2011-08-26
Hello All,

Yesterday exactly the same problem appears on my PC.
After incorrect shutdown (probably leak of electricity), Ubuntu didn't start up any more. The problem is the same like in **tdennist** case. System does not startup with the same error:

> EXT4-fs (sda3): INFO: recovery required on readonly filesystem
EXT4-fs (sda3): write access will be enabled during recovery
EXT4-fs warning (device sda3): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
EXT4-fs warning (device sda3): ext4_clear_journal_err: Marking fs in need of filesystem check
BUG: unable to handle kernel paging request at 013bd000Run from Live CD and fsck has the same effect like in** tdennist** case:

> fsck.ext4: Device or resource busy while trying to open /dev/sda3
Filesystem mounted or opened exclusively by another program?(but nothing was mounted at all).

My Ubuntu version is 10.04, kernel version is 2.6.32-33. The problem is, that I don't have any other kernels in my system, so I am not able to use   older one (e.g. 2.6.32-21-generic) like **tdennist**. I have only one Ubuntu Live CD (v10.04).

What should I do in my case? Download some older Ubuntu Live CD? Which version shall I use?

The reason I am not able to run fsck is that Live CD automatically mounts file system from hard drive if it is found. File system on my hard drive is damaged, and "mount" process hangs up. Device is unaccessible then. Of cource umount also doesn't work - it also hangs up.

New Ubuntu installation is also impossible - installation hangs up after second step (when accessing to hard drive).

So my question is - how to force live CD not to mount hdd file system during startup? If it is not possible, which version of Ubuntu Live CD shall I use to obey this problem? Or maybe this bug is fixed in newest Ubuntu version? What are your suggestions?

Removing partition is impossible in my case - too important are there

Greetings to All,
Grzegorz

---

