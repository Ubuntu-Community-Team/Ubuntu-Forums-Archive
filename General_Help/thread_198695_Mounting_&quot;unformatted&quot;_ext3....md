---
title: "Mounting &quot;unformatted&quot; ext3..."
date: 2006-06-17
forum: General Help
---

### Post by Bart123 on 2006-06-17
Hi everyody.
I installed 5.10 again on different HD, and  ofcourse wanted to mount and play with my old drive. Can't seem to work...
The desired device is hdb5, it gets recognized by the "disks manager" applet, which tells me that it is "unformatted"...  here you have the fdisk -l output.
Trying mounting it manually by "sudo mount -t ext3 /dev/hdb5  /media/old tell me that "/dev/hdb5 already mounted or /media/old busy".
All my goodoldstuff  is on that driver. What shold I do?
Many thanks ahead...
 
fdisk -l gives:
Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32        2434    19302097+   5  Extended
/dev/hdb5              32        2434    19302066   8e  Linux LVM

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  83  Linux
/dev/sda2   *        2551       19581   136801507+  83  Linux
/dev/sda3           19582       19929     2795310    5  Extended
/dev/sda5           19582       19929     2795278+  82  Linux swap / Solaris

---

### Post by Ocxic on 2006-06-17
i see that hdb5 in an LVM volume you prolly have a mount point in /dev/mappper/  I'm not sure how to manage lvms tho. mount as you would normally

---

### Post by Bart123 on 2006-06-18
As I mentioned, I already tries the way I'm used to.... No luck! Gettin the "already mounted or busy" reply...
Any other ideas?

---

### Post by Ocxic on 2006-06-18
paste the output of "mount" and dmesg after you've tried mounting.

---

### Post by Bart123 on 2006-06-18
I'm guessing some LVM problem...
Anyway:

ita@Jerald:~$ sudo mount -t ext3 /dev/hdb5 /media/old
mount: /dev/hdb5 already mounted or /media/old busy

ita@Jerald:~$ sudo dmesg
a0060/serio0).
[4346089.780000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346090.087000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346090.087000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346090.255000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346090.255000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346090.527000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346090.527000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346090.687000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346090.687000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346090.917000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346090.917000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346091.077000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346091.077000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346091.374000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346091.374000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346091.534000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346091.534000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346092.625000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346092.625000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346092.819000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346092.819000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346093.852000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346093.852000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346094.411000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346094.411000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346136.654000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346136.654000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346136.746000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346136.746000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346136.816000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346136.816000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346138.262000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346138.262000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346154.624000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346154.624000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346154.670000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346154.670000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346504.985000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346504.985000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.068000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346505.068000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.252000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346505.252000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.336000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346505.336000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.515000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346505.515000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.590000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346505.590000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.786000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346505.786000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346505.870000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346505.870000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346506.109000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346506.109000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346506.196000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346506.196000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346506.427000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346506.427000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346506.510000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346506.510000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346506.783000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346506.783000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346506.892000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346506.892000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346507.113000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346507.113000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346507.222000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346507.222000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346507.444000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346507.444000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346507.566000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346507.566000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346507.800000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346507.800000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346507.892000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346507.892000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346508.888000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346508.888000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346509.022000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346509.022000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346509.421000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346509.421000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346509.513000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346509.513000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346509.853000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346509.853000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346509.962000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346509.962000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346510.252000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346510.252000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346510.377000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346510.377000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346510.836000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4346510.836000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346510.953000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4346510.953000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4346761.018000] ra0: no IPv6 routers present
[4346858.613000] ra0: no IPv6 routers present
[4346941.295000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4346952.100000] eth0: no IPv6 routers present
[4347272.351000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4347272.351000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347272.443000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4347272.443000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347272.526000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4347272.526000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347272.630000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4347272.630000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347279.336000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4347279.336000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347279.444000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4347279.444000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347338.270000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4347338.270000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347338.413000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4347338.413000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347338.905000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4347338.905000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4347339.040000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4347339.040000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4348301.076000] ra0: no IPv6 routers present
[4353574.875000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4353574.875000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353574.959000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4353574.959000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.041000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4353575.041000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.117000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4353575.117000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.186000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4353575.186000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.278000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4353575.278000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.348000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4353575.348000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.436000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4353575.436000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.505000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4353575.505000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.589000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4353575.589000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.637000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4353575.637000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4353575.746000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4353575.746000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4354021.401000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4354021.401000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4354021.518000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4354021.518000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371609.418000] kjournald starting.  Commit interval 5 seconds
[4371609.418000] EXT3 FS on hdb1, internal journal
[4371609.418000] EXT3-fs: mounted filesystem with ordered data mode.
[4371670.540000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4371670.540000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371670.632000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4371670.632000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371673.358000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4371673.358000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371673.493000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4371673.493000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371781.779000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4371781.779000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371781.888000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4371781.888000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4371887.211000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4371887.211000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4371887.211000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4371887.454000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4371887.454000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4371887.454000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4372296.480000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4372296.480000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372296.572000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4372296.572000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372296.895000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4372296.895000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372297.038000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4372297.038000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372307.803000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4372307.803000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372307.891000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4372307.891000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372307.978000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4372307.978000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4372308.078000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4372308.078000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

---

### Post by Ocxic on 2006-06-18
just type "mount" and past the output.

---

### Post by Bart123 on 2006-06-18
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-686/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=itama

---

### Post by Ocxic on 2006-06-19
ok this -> /dev/hdb5 32 2434 19302066 8e Linux LVM

is saying that the partition is an LVM (logical volume managment) volume. therfor you can't just mount hdb5. check in /dev/mapper/ for your mount. 

so your line should look something like this: "sudo mount -t ext3 /dev/mapper/"your drive here" /media/old"

---

### Post by Bart123 on 2006-06-19
Ocxic you magnificent bastard!
It worked!
Thank you!
=D> =D> =D> =D>

---

### Post by DiGiTY on 2006-07-06
[QUOTE=Ocxic]ok this -> /dev/hdb5 32 2434 19302066 8e Linux LVM

is saying that the partition is an LVM (logical volume managment) volume. therfor you can't just mount hdb5. check in /dev/mapper/ for your mount. 

so your line should look something like this: "sudo mount -t ext3 /dev/mapper/"your drive here" /media/old"[/QUOTE]

worked like a charm, saved my ***!

thanks Ocxic

---

### Post by Salmonman on 2006-07-07
Just searching around for a solution to my Ralink (RT61) woes :-k

And its this i'm interested in:

> **Bart123 said:**
> 
[4346761.018000] ra0: no IPv6 routers present


I got the same error when I checked my dmesg.

I have followed all the instructions in [http://www.ubuntuforums.org/showthread.php?t=132980]("http://www.ubuntuforums.org/showthread.php?t=132980")
as far as I know (I'm using default ubuntu dapper 6.06) and I can see the card under network-manager, iwconfig and even see transfer activity in network-tools...

Other notable messages in the dmesg are:

```

rt61: module liscence 'unspecified' taints kernel
RT61: RfIcType = 3
ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver!

```

---

