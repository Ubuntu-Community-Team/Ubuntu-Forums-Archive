---
title: "/var on the same partition as /home"
date: 2010-04-16
forum: General Help
---

### Post by muszek on 2010-04-16
Summary: I want to have /var (and perhaps /tmp and/or /etc) to be on the same partition as /home.

Right now I have a simple setup.  7.4 GB /dev/sda2 mounted as / and 137 GB /dev/sda3 mounted as /home.  /var is important, because that's where I have tens of MySQL databases.  This setup causes several problems:
 * I'd like to have /var separately from / so that I can freely erase everything on /dev/sda2 and start over.
 * I'm running out of space (~800MB free) and I'm afraid that it might not be enough to dist-upgrade to Lucid.

I tried copying /var to /home/var and making a symlink to it, but that didn't work (had to reverse it from LiveUSB).

How should it be done properly?  I've read something about bind in fstab, but haven't found a straightforward solution.

that's my fstab:
```
# / was on /dev/sda2 during installation
UUID=6aaab958-6d51-41f1-8c07-e1139fc9b222 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=6aef255c-562b-4546-b0d4-1be330d55d12 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
#UUID=e9083f94-1bcb-4504-a413-4de3184cc442 none            swap    sw              0       0
```

---

### Post by KeyserSoze93 on 2010-04-16
Yeah, I'd bind from fstab. Boot a live system, copy your /var and /home to your new partition, and add a couple of lines like the following in fstab (assuming your second partition is /media/data):

```

/media/data/home   /home  none    defaults,bind   0 0
/media/data/var   /var  none    defaults,bind   0 0

```

Then, reboot into your real system. Run the mount command, and if the output looks right, boot into the live CD again and get rid of the old versions of /home and /var on /.

---

### Post by srs5694 on 2010-04-16
The /etc directory *must* reside on the root filesystem (/). The same is true of /bin, /sbin, and /lib (or /lib32 and /lib64). This is because these directories all contain critical files for mounting other filesystems and performing other critical and very basic tasks, such as /etc/fstab and /bin/mount.

---

### Post by muszek on 2010-05-01
I tried KeyserSoze93's solution.  Booted to a LiveUSB, copied /var to $big_partition/var, moved /home to $big_partition/home (and moved /var to /var-orig).
Then made changes to fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=6aaab958-6d51-41f1-8c07-e1139fc9b222 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=6aef255c-562b-4546-b0d4-1be330d55d12 /media/big           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e9083f94-1bcb-4504-a413-4de3184cc442 none            swap    sw              0       0

/media/big/var 		/var 	none defaults,bind 	0 	0
/media/big/home 	/home 	none defaults,bind 	0 	0

```

Rebooted.
Grub menu loaded.  Then the "loading splash screen" showed for a few seconds and I got an error, something like this: "error mounting a root filesystem".  I'm dropped on a console.  The root system is mounted read-only (so I can't even revert the changes... have to use the LiveUSB).

/media/big is the same partition I used for /home before.  I simply moved user dirs into $this_partition/home.  I also tried leaving /home as it was before, copying /var to /home/var and entering "/home/var 		/var 	none defaults,bind 	0 	0" in fstab - same error happened.

Any hints?

---

