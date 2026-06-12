---
title: "Mounting hda1."
date: 2005-02-23
forum: General Help
---

### Post by I am Jack's username on 2005-02-23
Ubuntu 5.04 array 3.5 live CD i386.

Created a folder called "suse" in /home/ubuntu with the GUI and then ran [COLOR=DarkGreen]mount -r -t ext3 /dev/hda1 /home/ubuntu/suse/[/COLOR] as root from /home/ which reports [COLOR=DarkRed]mount: /dev/hda1 already mounted or /home/ubuntu/suse/ busy[/COLOR].

I get [COLOR=DarkRed]umount: /dev/hda1: not mounted[/COLOR] and lsof doesn't give anything for /dev/hda1 or /home/ubuntu/suse/. 

Any suggestions on how to mount the harddisk?

---

### Post by scoon on 2005-02-23
Hey there, 

Open up a terminal and type mount to see just what is mounted. 

scoon

---

### Post by I am Jack's username on 2005-02-26
[QUOTE=scoon]Open up a terminal and type mount to see just what is mounted.[/QUOTE]

```
root@ubuntu:/home/ubuntu # mount
/dev/mapper/casper-snapshot on / type auto (rw,noatime)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
```

```
root@ubuntu:/home/ubuntu # cat /proc/mounts
rootfs / rootfs rw 0 0
/dev/cdroms/cdrom0 /cdrom iso9660 ro 0 0
/dev/mapper/casper-snapshot / ext2 rw,noatime 0 0
proc /proc proc rw,nodiratime 0 0
sysfs /sys sysfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/mapper/casper-snapshot /.dev ext2 rw,noatime 0 0
none /dev tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev 0 0
```

---

### Post by scoon on 2005-02-26
Hey there, 

What does your /etc/fstab look like ?


scoon

---

