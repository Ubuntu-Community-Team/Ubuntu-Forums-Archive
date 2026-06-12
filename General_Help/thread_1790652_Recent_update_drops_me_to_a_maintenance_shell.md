---
title: "Recent update drops me to a maintenance shell"
date: 2011-06-25
forum: General Help
---

### Post by shoan120 on 2011-06-25
I asked for help from another forum:
[http://www.techsupportforum.com/forums/f64/linux-error-cant-use-my-computer-581292.html](http://www.techsupportforum.com/forums/f64/linux-error-cant-use-my-computer-581292.html)
but they said to come here to fix the problem.

If its possible, I need it to be fixed by today. I have alot of music and videos that I want to save, so is there anyway I can save them.

I am really new to Linux and i don't really know how to use it, but I was running Ubuntu 10.04 and when i updated it it brang me to a black screen where i have to choose what to run. No matter what option I choose, I can't go back to regular use, even after restarting it. There is more details in the link I provided above.

---

### Post by blueridgedog on 2011-06-25
I assume you are booted off of a live CD.  For the sake of clarity, can you post the output of 

```
sudo fdisk -l 
```

and 

```
mount
```

Also, when you tried to mount your root partition, what error did you get?

---

### Post by shoan120 on 2011-06-25
when i press mount:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit =0)
proc on /proc type proc (rw,noexec, nosuid,nodev)
none on /sys type sysfs (rw,noexec, nosuid,nodev)
fusect1 on /sysfs/fuse/connection type fusect1 (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec, nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw, nosuid,nodev)
none on /var/run type tmpfs (rw, nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec, nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw, noexec, nosuid,nodev)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem) . It's possible that information reported by mount(8) is not up to date. For actual information about system mount points check the /proc/mounts file. 
```








when i press fdisk -l:
```
Disk /dev/sda: 250.1GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units= cylinders of 16065*512 = 8225280 bytes
Sector size (logical/physical) : 512 bytes / 512 bytes
I/O size (minimum/optimal): 512bytes/512bytes
disk identifier: 0x0009f598

Device Boot. Start. End. Blocks. Id. System
/dev/sda1. * 1. 29637. 238053376. 83. Linux
/dev/sda2. 29637. 30402. 6142977. 5. Extended
/dev/sda5. 29637. 30402. 6142976. 82. Linux swap/Solaris

```

---

### Post by blueridgedog on 2011-06-25
I am a bit confused by the output.

I see you have only one drive with three partitions

```
/dev/sda1. * 1. 29637. 238053376. 83. Linux
/dev/sda2. 29637. 30402. 6142977. 5. Extended
/dev/sda5. 29637. 30402. 6142976. 82. Linux swap/Solaris
```

Once is swap and one is an extended partition, leaving only one as a usable partition, sda1.

Additionally, sda1 is mounted as /.

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit =0)
```

Are you booted on a LiveCD or are you booted off of your system?

---

### Post by shoan120 on 2011-06-25
I am not really sure, I got the computer from a friend, he installed it and everything for me.

---

### Post by Yellow Pasque on 2011-06-25
You're running a 2.6.35 kernel, which is not a normal Lucid kernel (Lucid used 2.6.32). Is it possible that you upgraded to 10.10/Maverick?

---

### Post by shoan120 on 2011-06-25
I have no idea, it was asking me to update for a long time and i finally decided to do it, and then it comes to this

---

### Post by blueridgedog on 2011-06-26
> **shoan120 said:**
> I have no idea, it was asking me to update for a long time and i finally decided to do it, and then it comes to this

Is there a CDROM in your computer when you boot it?

---

