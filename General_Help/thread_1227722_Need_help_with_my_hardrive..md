---
title: "Need help with my hardrive."
date: 2009-07-31
forum: General Help
---

### Post by RwP_Icefalcon on 2009-07-31
I have windows 7 and ubuntu on the same hardrive.  I have them both partitioned on the D: drive.  I also have other files like music, and video files on that hardrive. (Not in windows, just on the actual hardrive). Is there anyway i can get into that hardive in ubuntu?

---

### Post by dcstar on 2009-07-31
> **RwP_Icefalcon said:**
> I have windows 7 and ubuntu on the same hardrive.  I have them both partitioned on the D: drive.  I also have other files like music, and video files on that hardrive. (Not in windows, just on the actual hardrive). Is there anyway i can get into that hardive in ubuntu?

The drive should be in your Places menu.

---

### Post by MaxIBoy on 2009-07-31
If the system is actually working, you ought to be seeing the partitions already.

Could you post the output of the following console commands:
```
cat /etc/fstab
```
```
cat /etc/mtab
```
```
ls /dev/*d*
```

---

### Post by RwP_Icefalcon on 2009-07-31
```
tom@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


``````
tom@ubuntu:~$ cat /etc/mtab
/host/ubuntu/disks/root.disk / ext3 rw,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
/dev/sda3 /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-14-generic/volatile tmpfs rw,mode=755 0 0
/host/ubuntu/disks/boot /boot none rw,bind 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tom/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tom 0 0
/dev/sdb1 /media/Koyuki fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda2 /media/ACER fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

``````
tom@ubuntu:~$ ls /dev/*d*
/dev/adsp             /dev/nvidiactl  /dev/sde             /dev/usbdev2.1_ep00
/dev/audio            /dev/oldmem     /dev/sdf             /dev/usbdev2.1_ep81
/dev/cdrom            /dev/random     /dev/sndstat         /dev/usbdev2.2_ep00
/dev/cdrw             /dev/scd0       /dev/stderr          /dev/usbdev2.2_ep81
/dev/cpu_dma_latency  /dev/sda        /dev/stdin           /dev/usbdev2.2_ep82
/dev/dsp              /dev/sda1       /dev/stdout          /dev/usbdev2.3_ep00
/dev/dvd              /dev/sda2       /dev/urandom         /dev/usbdev2.3_ep81
/dev/dvdrw            /dev/sda3       /dev/usbdev1.1_ep00  /dev/usbdev2.4_ep00
/dev/hidraw0          /dev/sdb        /dev/usbdev1.1_ep81  /dev/usbdev2.4_ep01
/dev/hidraw1          /dev/sdb1       /dev/usbdev1.4_ep00  /dev/usbdev2.4_ep82
/dev/hidraw2          /dev/sdc        /dev/usbdev1.4_ep02
/dev/nvidia0          /dev/sdd        /dev/usbdev1.4_ep81

/dev/disk:
by-id  by-label  by-path  by-uuid

/dev/fd:
0  1  2  3

/dev/pktcdvd:
control

/dev/snd:
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  pcmC0D2c  seq  timer

```

---

### Post by MaxIBoy on 2009-07-31
Looking at what you've posted, you seem to have installed Ubuntu through wubi, the tool that lets you install it as if it were a Windows program.

In which case, try going to the "/host" directory to get at your Windows files.

[LIST]
[*]It should be in the "places" menu under the name "host" or similar.
[*]If you go to "places" and then "computer," you should also see it there.
[*]Finally, if you pull up a file browser and manually enter the path "/host" you are guaranteed to get there that way.
[/LIST]

It also looks like you have other partitions mounted as well, specifically /media/Koyuki and /media/ACER. These can be accessed similarly to how you can access "/host".

---

### Post by RwP_Icefalcon on 2009-07-31
> **MaxIBoy said:**
> Looking at what you've posted, you seem to have installed Ubuntu through wubi, the tool that lets you install it as if it were a Windows program.

In which case, try going to the "/host" directory to get at your Windows files.

[LIST]
[*]It should be in the "places" menu under the name "host" or similar.
[*]If you go to "places" and then "computer," you should also see it there.
[*]Finally, if you pull up a file browser and manually enter the path "/host" you are guaranteed to get there that way.
[/LIST]

It also looks like you have other partitions mounted as well, specifically /media/Koyuki and /media/ACER. These can be accessed similarly to how you can access "/host".
Thank you so much man.  It wasnt under places for some reason.  I looked there before I came here.

---

