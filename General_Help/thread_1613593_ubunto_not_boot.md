---
title: "ubunto not boot"
date: 2010-11-04
forum: General Help
---

### Post by etzioni on 2010-11-04
without any apperant reason the ubuntu could not be started, The computer loaded to  a prompt page with several error indication and  and the lines beginning was:

(initramfs) ....


I enter with a LIVECD and try to mount to the root partition

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac38ac38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38256   307291288+  83  Linux
/dev/sda2           38257       38913     5277352+   5  Extended
/dev/sda5           38257       38913     5277321   82  Linux swap / Solaris
I tried to mount sda1 but the command

> ubuntu@ubuntu:~$ sudo mount /dev/sda1  /mntsimply got stuck, the terminal will not response after this. 

So I'm pretty stuck, I have no idea how to save my old file and how to try recover the ubuntu installation.

---

### Post by etzioni on 2010-11-05
also:

> ubuntu@ubuntu:~$ sudo mount /dev/sda1  /mnt -t vfat
mount: /dev/sda1 already mounted or /mnt busy

anyone?

---

### Post by Rubi1200 on 2010-11-05
Hi,
from the LiveCD, post the results of the boot-script linked at the bottom of my post.

Please wrap the text with the code # tag when posting back.

Thanks.

(by the way, I do not think that using vfat as the option after the -t switch will work since the file-system type on sda1 is most likely ext3 or ext4: see man mount for a better description).

---

### Post by etzioni on 2010-11-05
I downloaded the script and run it:

```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 

...

```

and nothing happened for at least 10 minutes

---

### Post by Rubi1200 on 2010-11-05
Did you put the script on the Desktop before running the command?

Give it another try; it should only take a couple of minutes at most to generate the RESULTS.txt file.

---

### Post by etzioni on 2010-11-05
Obviously, other wise I would get 'No such file or directory'.

I tried it again for two more times. and nothing it simply stuck.

---

### Post by etzioni on 2010-11-05
Does that make any sense?

```
sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

what does it mean?

---

### Post by Rubi1200 on 2010-11-05
Try unmounting all file-systems including swap and see if it makes a difference. Also, if you have any external devices plugged in you may want to disconnect them and see if that helps.

---

### Post by etzioni on 2010-11-05
> **Rubi1200 said:**
> Try unmounting all file-systems including swap and see if it makes a difference. Also, if you have any external devices plugged in you may want to disconnect them and see if that helps.

I already tried:


```
ubuntu@ubuntu:~$ sudo umount /dev/sda1 /mnt
umount: /dev/sda1: not mounted
umount: /mnt: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda5 /mnt
umount: /dev/sda5: not mounted
umount: /mnt: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda1 
umount: /dev/sda1: not mounted

```

---

### Post by etzioni on 2010-11-05
```
umount -a 
```

apparently does try something but also got stuck



```
ubuntu@ubuntu:~$ sudo umount -f /dev/sda1 
umount2: Invalid argument
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo umount -a -f /dev/sda1 
umount2: Device or resource busy
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
umount: /tmp: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
umount: /rofs: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


..... [ Terminal get stuck ]


```

---

### Post by Rubi1200 on 2010-11-05
I am sorry, but I don't know what to tell you.

The only thing I can think of was that there was/is some kind of file-system error which caused this in the first place.

If you are willing, we can try and repair the file-system from the LiveCD and see if that helps.

Either that or wait and see if others have different suggestions.

Here are the commands:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

If there are errors reported then run:

```
sudo e2fsck -f -y -v /dev/sda1
```

---

### Post by etzioni on 2010-11-05
the first, obviously:


```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```


the second, the same:

```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

---

### Post by Rubi1200 on 2010-11-05
Hmm,
what does the output of ```
cat /proc/mounts
``` show?

---

### Post by etzioni on 2010-11-05
> **Rubi1200 said:**
> Hmm,



```
ubuntu@ubuntu:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=894524k,nr_inodes=216124,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
aufs / aufs rw,noatime,si=6def992e 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0

```

---

### Post by Rubi1200 on 2010-11-05
I don't know what to tell you etzioni; sorry.

This is the output I get from the LiveCD running the command:
```
ubuntu@ubuntu:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=500172k,nr_inodes=125043,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/sdb1 /cdrom vfat ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
aufs / aufs rw,noatime,si=11906015 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
```

As you can see, there is quite a difference.

Something is either mounting your partition or holding it locked. Did you do a forced shutdown before all this trouble started?

Do you remember what was going on at the time; programs open, updates etc?

---

### Post by Quisling on 2011-02-03
Sorry to necro this, but I'm having identical results for EVERY command.  My filesystem is apparently locked as "in-use" with no way to fix what is (apparently) a bad superblock.  I have tried each of the steps so far in this thread, with no results.

Prior to this happening, on shutdown the computer hung on a black screen for about an hour, after which time I forced shutdown.  Now I am having this issue.

Is there anyway to de-flag the partition (or entire device) as "in-use" to force fsck or e2fsck to work?

---

