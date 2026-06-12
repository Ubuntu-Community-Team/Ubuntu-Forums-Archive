---
title: "No loopback device available"
date: 2009-08-11
forum: General Help
---

### Post by DouglasCaixeta on 2009-08-11
I'm  using TrueCrypt and I'm trying to mount a file that I already have, and I already mounted thousand of times without any problem.

But now, when I try to mount I get the error: "No loopback device available."

What is that? How can I solve this?

---

### Post by michy99 on 2009-08-11
Are you trying to mount by command line or using the GUI? Also, what is the output of```
mount
```

---

### Post by DouglasCaixeta on 2009-08-11
I'm using the GUI.

Here is the output:

```
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda6 on /mnt/data type ext3 (rw,relatime)
/mnt/data on /mnt/data type dazukofs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/caixeta/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=caixeta)
/dev/mmcblk0 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

---

### Post by michy99 on 2009-08-11
What happens if you try to mount from the command line?```
sudo truecrypt /path/to/truecrypt/volume /path/to/mountpoint
```

---

### Post by dandnsmith on 2009-08-11
If you get the 'no loopback device available' then there isn't one available (just as it says) and you may have to create some more.

I've done this some years ago, but have forgotten the precise commands to do it - an examination of the man pages related to loop devices might give the data (that's where I think I got it).

---

### Post by DouglasCaixeta on 2009-08-11
> **michy99 said:**
> What happens if you try to mount from the command line?

I got the same error.

> If you get the 'no loopback device available' then there isn't one available (just as it says) and you may have to create some more.

What is loopback device? Why is not available anymore? Is not that I'm mounting a thousands of devices at the same time.

---

### Post by dandnsmith on 2009-08-12
A loopback device is a virtual device, usually you see it under /dev (look for things like /dev/loop), and it gets used for mounting things like .iso files.

By default, there are a limited number created at install time - I've no idea what the standard is for the distros these days, but I had to create more than the one present at the time to which I referred.

---

### Post by DouglasCaixeta on 2009-08-13
And how can I create more loop devices?

I tried this tutorial but nothing: [http://www.brandonhutchinson.com/Creating_additional_loop_devices.html](http://www.brandonhutchinson.com/Creating_additional_loop_devices.html)

I think my problem is another one. Cause when I type this command:

```
/sbin/rmmod loop
```

I receive the following:

```
ERROR: Module loop does not exist in /proc/modules
```

The only different thing that I made in my computer: I installed the "AntiVir Guard". And this program installed Dakuzo. Maybe there is something to do, I don't know.

I just need to acess my TrueCrypt file, cause there is important information there.

---

### Post by DouglasCaixeta on 2009-08-13
I uninstalled Antivir Guard, but still the same. So I uninstalled TrueCrypt, which was 6.1a, and installed 6.2a.

No I got this error:

```
Failed to set up a loop device
```

---

### Post by michy99 on 2009-08-13
Just something to try. Boot from a live cd. Install truecrypt. Try to mount truecrypt volume.

---

### Post by DouglasCaixeta on 2009-08-13
Didn't try that yet.

I install now 5.1, and its working! So strange.

---

### Post by qweeak on 2011-12-24
Hey,

You can create loop back device by mknod.
---
mknod -m 660 /dev/loop8 b 7 8
chown root.disk /dev/loop8
---

---

