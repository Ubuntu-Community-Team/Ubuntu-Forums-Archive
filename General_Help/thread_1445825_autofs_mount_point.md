---
title: "autofs mount point"
date: 2010-04-03
forum: General Help
---

### Post by psankovic on 2010-04-03
Hi,

Can someone help me. With autofs I mounter one computer disk to another, but when I boot my computer my mount point is missing. 
If I mount directory manually /mnt/xxxxx directory apears and I can access other computer disk. After some time directory dissapear again ( which is normal due to autofs ), but mount point is missing as well. I can not access it using file manager I need to mount it again using terminal.
????

/thanks,

---

### Post by thebigob on 2010-04-03
With automounter the directory should dissappear when it is not mounted.

In your case you tell the mounter to auto mount at /mnt

so if you cd to /mnt and do ls you will see nothing.

You know it will mount to XXXX

so you try cd XXXX

this should then mount the disk and it will then be available to use.

After some time this will unmount again.

An example of this here: 

```

root@SheevaPlug:~# mount
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/mmcblk0p1 on /media/SD type ext3 (rw,noatime)
root@SheevaPlug:~# cd /auto
root@SheevaPlug:/auto# ls
root@SheevaPlug:/auto# cd erv
root@SheevaPlug:/auto/erv# mount
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/mmcblk0p1 on /media/SD type ext3 (rw,noatime)
/dev/sda1 on /auto/erv type ext3 (rw,noatime,commit=600,data=ordered,barrier=1)
root@SheevaPlug:/auto/erv# cd
root@SheevaPlug:~# cd /auto
root@SheevaPlug:/auto# ls
root@SheevaPlug:/auto# mount
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/mmcblk0p1 on /media/SD type ext3 (rw,noatime)
root@SheevaPlug:/auto# 


```

---

### Post by psankovic on 2010-04-03
Hi,

Thanks. It's working.

/regards,

---

